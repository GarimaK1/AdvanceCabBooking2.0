Note:
This project requires Paypal to run. Use file "paypal-credentials" which contains sandbox details.

Two roles only: 'admin' and 'loggedUser'
Admin Username: admin@123.com
Admin Password: admin
-----------------------------------------------------------------------------------------------------------
Styling:
-- Angular Material
-- Angular Flex Layout "FlexLayoutModule"

-----------------------------------------------------------------------------------------------------------
During login:
-- check if credentials match with ones in DB. using- "login", "authService", "userRoutes"
-- if credentials are valid, create authorization token at backend "userRoutes.js" and
    get it at frontend "auth.service.ts"

All requests leaving frontend:
-- After login, due to "auth-interceptor.ts" all requests leaving frontend carry that token now.
-- Token is inside "Authorization" header

Requests reaching backend:
-- For some routes that need to be protected using authentiation token, "check-auth.js" middleware is added.
-- It is added before req is processed.
-- It is a middleware that verifies the token.
-- If token is correct, the req is allowed to complete.
-- If token is incorrect, 401 authentication failed error is thrown.

-------------------------------------------------------------------------------------------------------------
Problem with Payment and Edit ScheduleCabForm:
-- Changing the number of passengers, pickup or drop location means route update.
-- Route update means distance, tolls, etc. So re-computation of fare.
-- At present application doesn't support that.
Solution:
a) Let customer pay $10 to confirm booking. Balance payable after travel.
   But then the distance that we calculated earlier is not used in our app.
   So implementing option (b).
b) Set condition in edit schedule cab form: user cannot update these fields.

-------------------------------------------------------------------------------------------------------------
-- Created two new modules to condense related work together:
   AuthModule, AngularMaterialModule
-- Using AuthModule (Login & Signup components) for Lazy Loading

-------------------------------------------------------------------------------------------------------------
Boolean vs boolean in Typescript e.g. while explicitly assigning return types
-- Upper case Boolean is an object type whereas lower case boolean is a primitive type.
-- It is always recommended to use boolean, the primitive type in your programs.
-- This is because, while JavaScript coerces an object to its primitive type,
-- the TypeScript type system does not. TypeScript treats it like an object type.

-------------------------------------------------------------------------------------------------------------
Token stored in angular authService needs to be stored somewhere other than angular to persist.
Otherwise when we reload any page i.e. reload angular application, memory is wiped clean
and we lose that token.
So stored it in local storage(provided by browser).

-------------------------------------------------------------------------------------------------------------
-- Inside AuthInterceptor
intercept method is called for all "http requests" leaving angular. So kind of middleware on front-end.
injecting token into outgoing requests.
The Basic Authentication Interceptor intercepts http requests from the application to add
basic authentication credentials to the Authorization header if the user is logged in.

--Inside ErrorInterceptor
Most major errors thrown in this application are http errors, sent as response by backend.
Interceptor "handle" method can be used to handle incoming response errors.

-------------------------------------------------------------------------------------------------------------
Deployment Notes:
Deployed using AWS Elastic Beanstalk for backend API and S3 for angular frontend.
For deployment of backend:
Created application, created environment - created environment variables, under modify software - mentioned command to start node process. In newer version of AWS, add procfile(web: node server.js) to the zipped file to upload to cloud.
For deployment of frontend:
Updated src/environments/enironment.prod.ts file with apiUrl.
Created dist folder using command "ng build --prod".
Created S3 bucket with public access to upload contents of dist folder.

-------------------------------------------------------------------------------------------------------------
Changes to be done in future:
-- Remove types: ["address"] from 'book-online.component.ts' and 'book-online-edit.component.ts'
-- Make site more responsive. Easily done using flex-layout in component css and following changes to 'app.component.css'-
e.g.
/* Medium devices (tablets, less than 959px)
@media (max-width: 959px) {
  div {
    flex: 1 0 auto;
    margin: auto;
    margin-top: 1rem;
    margin-bottom: 1rem;
    width: 90%;
  }
}
Large devices (desktops, 960px and up)
@media (min-width: 960px) {
  div {
    flex: 1 0 auto;
    margin: auto;
    margin-top: 1rem;
    margin-bottom: 1rem;
    width: 60%;
  }
} */

-------------------------------------------------------------------------------------------------------------
References:

https://www.udemy.com/course/angular-2-and-nodejs-the-practical-guide/learn/lecture/14852496?start=210#overview
-------------------------------------------------------------------------------------------------------------

Notes 15 December 2021:
Deploying the app to heroku as a node app, as AWS account is closed.
Added heroku as remote
Added Procfile with start command
Added 'heroku-postbuild' in package.json
Added 'engines' entry in package.json
Heroku doesn't install devDependencies. So we can't use nodemon in production.
  So, removed nodemon.json file.
  Using heroku config vars on Heroku dashboard now for storing db credentials and jwt key

For old environment variables:
https://github.com/GarimaK1/AdvanceCabBooking2.0/blob/477bda85d76a477e1015d3a4f5bb37d6010f6411/nodemon.json
-------------------------------------------------------------------------------------------------------------
Hiding API key on Angular
https://indepth.dev/tutorials/angular/inject-environment-variables
https://www.freecodecamp.org/news/private-api-keys/

-------------------------------------------------------------------------------------------------------------
