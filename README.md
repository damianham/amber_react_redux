# amber_react
Amber web framework application recipe for a React/Redux SPA with Granite ORM

## NOT READY YET - do not use


A React/Redux SPA using [React](https://reactjs.org) and [Redux](https://reduxjs.org) library.
The amber backend serves both html and json.  Also includes a JWT authorisation
pipe in src/pipes.  Create a new amber app with this template with these commands;


```
amber new mynewapp -r damianham/amber_react_redux
cd mynewapp
amber g auth User
amber g scaffold Category title:string user:reference
amber g scaffold Product title:string description:text category:reference user:reference
amber g scaffold Comment body:text product:reference user:reference
```

### Notes

1. Remove the Authenticate pipe from `config/routes.cr` after generating the auth plugin.  
2. Uncomment AuthenticateJWT pipe from `config/routes.cr` if authentication is required.
3. If you're using [JWT](https://jwt.io/) then a `user_id` field is required on your **models**, **param validators** and **migrations** to render `edit` and `delete` buttons according to `current_user`.
4. By default this recipe doesn't provide a form to generate the JSON Web Token, but just to sign in. To generate a token you can use https://jwt.io/ or create your own form using JWT package, with your `secret_key_base` inside your `config/enviroments/development.yml` file and a valid email. Try `amber db seed` and email `admin@example.com`.
5. If you're getting "Could not load..." error then ensure your models URLs are inside `REGEX_PATHS` in `pipes/authenticate_jwt.cr`.
