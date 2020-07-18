## Project Description

AdvanceCabBooking is a single-page MEAN stack application developed on Angular8 for private cab owners so customers can book cabs online

MEAN = MongoDB, Express, Angular, Node

**Features**: 

• Developed REST API following MVC architecture to handle user data, contact forms and cab bookings

• Ensured role-based authentication and authorization utilizing custom middleware, route guards, JWT

• Crafted feature modules for organizing Angular Material components and "auth" components

• Decreased load times by adopting lazy loading technique

• Incorporated dynamic component loading for modals and snack-bars to display notifications

• Integrated Google Places API for auto-populating addresses

• Introduced PayPal smart payment buttons for cab payments

### To schedule a cab -

1. Schedule cab as guest (no login, cannot view or edit cab bookings)

2. Sign-Up, Login and schedule cab (can view & edit cab bookings)

**Note**: 

You will need dummy paypal credentials given above to complete payment for booking a cab.

Please don't use real paypal credentials!

## To explore this app:

### Explore using dummy credentials -

**Login**: gari@gmail.com

**Password**: gari

### PayPal Dummy Credentials to complete payment -

**Email**: sb-msefw972996@personal.example.com

**Password**: /t8.0xD^

### File "garimaReadme.txt" has my notes about this project.

### Refer file "paypal-credentials" for full Paypal Sandbox credentials

 -- required to successfully complete end-to-end flow for new cab booking.
 
### Visit website: http://advancecabbooking2.0.s3-website-us-east-1.amazonaws.com/

# AdvanceCabBooking

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 8.3.21.

Do not use Angular 9 to use this project. Will throw error. 

In case you update the dependencies, run command "npm i @angular-devkit/build-angular@0.803.23" to downgrade to req angular version.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
