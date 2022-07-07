# ANGULAR 13  (formerly "Angular 2") -DOCS
              reactive web apps with the successor of Angular.js
              
References:

       LTS version:  https://nodejs.org/en/
       Angular commands: https://angular.io/cli
Pligins:  
       emmet

UI : http://localhost:4200/


# Angular APP

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 14.0.4.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.


# CLI Deep Dive and troubleshooting
        Commands:
        $ sudo npm install -g npm. (sudo required for mac/linux)
        $ npm cache verify
        $ sudo npm install -g @angular/cli
        
        common issues & solutions:

        Creation of a new project takes forever (longer than 3 minutes)
        That happens on Windows from time to time => Try running the command line as administrator

        You get an EADDR error (Address already in use)
        You might already have another ng serve process running - make sure to quit that or use ng serve --port ANOTHERPORT  to serve your project on a new port

        My changes are not reflected in the browser (App is not compiling)
        Check if the window running ng serve  displays an error. If that's not the case, make sure you're using the latest CLI version and try restarting your CLI
        
# Creating a project
        $ ng new my-first-app --no-strict
        would you like to add angular routing - no
        select CSS
        Type Script is superset of Java script
        $ cd my-first-app
        $ ng serve
        
        $ git init
        $ git config --global user.name "abhilashgd"
        $ git config --global user.email "anrewgd@gmail.com"
        $ git add --all
        $ git commit -m "Initial Commit"
        $ git remote add origin ssh://git@
        $ git push -u origin HEAD:master
        
        replace app.component.html
        server runs on : http://localhost:4200/

# Editing the app
        FILE: app.component.html
        
               <input type="text" [(ngModel)]="name">
                     <p>{{ name }}</p>
              
        FILE: app component.ts
        
               import { Component } from '@angular/core';

                     @Component({
                       selector: 'app-root',
                       templateUrl: './app.component.html',
                       styleUrls: ['./app.component.css']
                     })
                     export class AppComponent {
                       name = 'abhilashgd';
                     }
        
       FILE: app.module.ts
       
              import { NgModule } from '@angular/core';
              import { BrowserModule } from '@angular/platform-browser';
              import { FormsModule } from '@angular/forms';
              import { AppComponent } from './app.component';

              @NgModule({
                declarations: [
                  AppComponent
                ],
                imports: [
                  BrowserModule,
                  FormsModule
                ],
                providers: [],
                bootstrap: [AppComponent]
              })
              export class AppModule { }

# BOOTSTRAP CSS Project

       $ npm install --save bootstrap@3
       GOTO-->angular.json
       add bootstrap css path
        "styles": [
              "node_modules/bootstrap/dist/css/bootstrap.min.css",
              "src/styles.css"
            ],
       $ ng serve
       --> open  http://localhost:4200/
       --> inspect element 
       we should see styles.css being imported in head
       <link rel="stylesheet" href="styles.css">
       under sources we should see styles.css
       and should contain "Bootstrap v3.4.1 (https://getbootstrap.com/)"
       
       If you're getting errors when running npm install, you can often solve them by running npm install --legacy-peer-deps instead of npm install
       
# Basics
       index.html --> contains app-root in the body which loads app root component --> app.component.ts
       main.ts --> platformBrowserDynamic().bootstrapModule(AppModule)--> amm.module.ts
       angular in the end is JS framework changing our DOM (HTML) at runtime
       
       FILE: app.component.ts
       
       
              Best PracticeL Each Component should typically have its own folder
              create appd--> server folder --> server.component.ts
              create appd--> server folder --> server.component.html

              FILE: server.component.ts
              import { Component } from "@angular/core";

              @Component({
                  selector: 'app-server',
                  templateUrl: './server.component.html'
              })
              export class ServerComponent {

              }
       
       FILE : app.module.ts
       
              import { NgModule } from '@angular/core';
              import { BrowserModule } from '@angular/platform-browser';
              import { AppComponent } from './app.component';
              import { ServerComponent } from './server/server.component';

              @NgModule({
                declarations: [
                  AppComponent,
                  ServerComponent
                ],
                imports: [
                  BrowserModule
                ],
                providers: [],
                bootstrap: [AppComponent]
              })
              export class AppModule { }

       FILE: server.component.html
            <h3>The Server Component</h3>
            
       FILE: app.component.html
            <h3>I am in the app component!</h3>
            <hr>
            <app-server></app-server>

# Creating component with CLI and nesting
      $ ng generate component servers
      or
      $ ng g c servers
      
      FILE: servers.component.html
            <app-server></app-server>
            <app-server></app-server>
      FILE: app.component.html
            <h3>I am in the app component!</h3>
            <hr>
            <app-servers></app-servers>
            
       when we inspect in http://localhost:4200/
       
       <app-root _nghost-ppn-c13="" ng-version="14.0.4">
       <h3 _ngcontent-ppn-c13="">I am in the app component!</h3>
       <hr _ngcontent-ppn-c13="">
       <app-servers _ngcontent-ppn-c13="" _nghost-ppn-c12="">
            <app-server _ngcontent-ppn-c12="">
            <h3>The Server Component</h3></app-server>
       <app-server _ngcontent-ppn-c12="">
            <h3>The Server Component</h3>
       </app-server></app-servers></app-root>
            
            
