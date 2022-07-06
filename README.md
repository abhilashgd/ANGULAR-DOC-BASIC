# ANGULAR-DOCS

References:

       LTS version:  https://nodejs.org/en/
       Angular commands: https://angular.io/cli

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

