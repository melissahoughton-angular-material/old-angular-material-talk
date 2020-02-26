# How to set up a new Angular app using Angular Material

1. Run the following commands:
    ```
    ng new my-app
    cd my-app
    ng add @angular/material
    ```

    `ng new my-app` generates the default Angular CLI starter template, you can replace  `my-app` with whatever you want to call your app

    Select `Y` for routing

    Select `SCSS` for styles

    `ng add @angular/material` will install the `@angular/cdk` and `@angular/material` libraries as well as adding setting up fonts and base styles

    In this example you can choose any of the default themes provided

    Select `Y` for animations

2. Remove the default Angular App content

    Remove everything in `app.component.html` except for `<router-outlet></router-outlet>`

3. Add in the material module
    Create folder called `material` your `src\app`

    Copy this file from my [github](https://github.com/melissahoughton/material.module/blob/master/material.module.ts) into the folder

4. Add `MaterialModule` to your app imports
    ```
    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';

    import { AppRoutingModule } from './app-routing.module';
    import { AppComponent } from './app.component';
    import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
    import { MaterialModule } from './material.module';

    @NgModule({
    declarations: [
        AppComponent
    ],
    imports: [
        BrowserModule,
        AppRoutingModule,
        BrowserAnimationsModule,
        MaterialModule
    ],
    providers: [],
    bootstrap: [AppComponent]
    })
    export class AppModule { }
    ```
6. Add some base styles into your app.

    Wrap the `<router-outlet></router-outlet>` tag in a div with a class `container`
    The add into your `app.component.scss `
    ```
    .container {
      max-width: 800px;
      margin: 4em auto;
      padding: 0 20px;
    }

    .container>* {
      display: flex;
      flex-direction: column;
      justify-content: center;
    }
    ```

    This gives us the basis of a flex layout.

Your app is now ready to use angular material. Set up using the components that work best for you. To continue with an example follow the steps in the next section.

***

# Create an Example Blog App in Angular Material

1. Add your first component and set up the route

    Run `ng generate component home`

2. Set up the routes

    Replace the empty routes in `app.routing.module.ts` with
    ```
    const routes: Routes = [
      { path: '', component: HomeComponent },
      { path: '**', redirectTo: '/', pathMatch: 'full' }
    ];
    ```

3. Add in the first material components

   In this example, I am going to set up a blog and want my home page to have card like previews of each post.
   Add in the following to `home.html` to start setting this up with angular material

   ```
   <h1>My Blog</h1>
    <mat-card>
        <mat-card-header>
            <mat-card-title>Easy, Breezy, Beautiful</mat-card-title>
            <mat-card-subtitle>Angular Material</mat-card-subtitle>
        </mat-card-header>
        <mat-card-content>
            <p>
                This is an amazing blog on angular material. Here is some awesome text about that. Here is some awesome text
                about that.
                Here is some awesome text about that. Here is some awesome text about that. Here is some awesome text about
                that.
                Here is some awesome text about that. Here is some awesome text about that. Here is some awesome text about
                that.
            </p>
        </mat-card-content>
        <mat-card-actions>
            <button mat-button>Like</button>
            <button mat-button>Read More</button>
        </mat-card-actions>
    </mat-card>
   ```

4. Run `ng serve` to see your new app

We can already see some of the material design styles but it is still a bit plain

***

# Test

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 9.0.2.

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
