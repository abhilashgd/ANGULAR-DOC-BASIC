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
            
# Component templates
      FILE: servers.component.ts
      
            import { Component, OnInit } from '@angular/core';

            @Component({
              selector: 'app-servers',
              template: `
              <app-server></app-server>
              <app-server></app-server>`,
              styleUrls: ['./servers.component.css']
            })
            export class ServersComponent implements OnInit {

              constructor() { }

              ngOnInit(): void {
              }

            }

# Component Styles

      FILE: app.component.html
      
            <div class="container">
            <div class="row">
                <div class="col-xs-12">
                    <h3>I am in the app component!</h3>
                    <hr>
                    <app-servers></app-servers>        
                </div>
            </div>
            </div>
      //external file css      
      FILE: app.component.css
                    h3 {
                  color:blue
              }
              
      //Inline style
      FILE: app.component.ts
            import { Component } from '@angular/core';

            @Component({
              selector: 'app-root',
              templateUrl: './app.component.html',
              //styleUrls: ['./app.component.css']
              styles: [`
              h3 {
                color: dodgerblue;
              }
              `]
            })
            export class AppComponent {
              name = 'abhilashgd';
            }

# Component Selector
      FILE: app.component.ts
            @Component({
              // selector: '[app-servers]',
             selector: 'app-servers',
             
      FILE: app.component.html
      
           <app-servers></app-servers>    
           <!-- <div app-servers></div>    -->
           <!-- <div class="app-servers"></div> -->
           
# Data binding
      Data binding = communication
      TypeScript code -->output data --> HTML
            String Interpolation ({{ data }})
            Property binding ( [property = "data"]
      HTML Code --> TypeScript
            Event Binding (React to user events) ( (event) = "exression")
            
       Combination of both - Two way binding ( [ (ngModel)] = "data" )
       
            import { Component } from "@angular/core";
 
 **String Interpolation**    
    
      FILE: server.component.ts
           import { Component } from "@angular/core";

            @Component({
                selector: 'app-server',
                templateUrl: './server.component.html'
            })
            export class ServerComponent {
                serverId: number = 10;
                serverStatus: string = 'offline';

                getServerStatus() {
                return this.serverStatus;
                }
            }
            
      FILE: server.component.html
           <p>Server with ID {{ serverId }} is {{ getServerStatus() }}</p>
           
  **Property binding**  
  
      FILE: servers.component.html
      
        <button class="btn btn-primary"
        [disabled]="!allowNewServer">Add Server</button>
        <app-server></app-server>
        <app-server></app-server>
        
      FILE: servers.component.ts
      
           import { Component, OnInit } from '@angular/core';

            @Component({
              // selector: '[app-servers]',
             selector: 'app-servers',
              // template: `
              // <app-server></app-server>
              // <app-server></app-server>`,
              templateUrl: './servers.component.html',
              styleUrls: ['./servers.component.css']
            })
            export class ServersComponent implements OnInit {
              allowNewServer = false;
              constructor() {
                setTimeout(() => {
                  this.allowNewServer = true;
                },2000);

               }

              ngOnInit(): void {
              }

            }

  **Event Binding**
  
      FILE: servers.component.html
          <button class="btn btn-primary"
        [disabled]="!allowNewServer"
        (click)="onCreateServer()">Add Server</button>
        <!-- <p [innerText]="allowNewServer"></p> -->
        <p>{{serverCreationStatus}}</p>
        <app-server></app-server>
        <app-server></app-server>

      FILE: servers.component.ts
      
          import { Component, OnInit } from '@angular/core';

            @Component({
              // selector: '[app-servers]',
             selector: 'app-servers',
              // template: `
              // <app-server></app-server>
              // <app-server></app-server>`,
              templateUrl: './servers.component.html',
              styleUrls: ['./servers.component.css']
            })
            export class ServersComponent implements OnInit {
              allowNewServer = false;
              serverCreationStatus = 'No server was created!';
              constructor() {
                setTimeout(() => {
                  this.allowNewServer = true;
                },2000);

               }

              ngOnInit(): void {
              }
            onCreateServer(){
              this.serverCreationStatus = 'server was created!';
            }
            }
           
           How do you know to which Properties or Events of HTML Elements you may bind? You can basically bind to all Properties and Events - a good idea is to console.log()  the element you're interested in to see which properties and events it offers.

      Important: For events, you don't bind to onclick but only to click (=> (click)).

      The MDN (Mozilla Developer Network) offers nice lists of all properties and events of the element you're interested in. Googling for YOUR_ELEMENT properties  or YOUR_ELEMENT events  should yield nice results.
      
 **Passing and Using data with event binding**
 
    FILE: servers.component.html
             <label>Server Name</label>
            <input type="text" class="form-control"
            (input) = "onUpdateServerName($event)">
            <p>{{serverName}}</p>

            <button 
                class="btn btn-primary"
                [disabled]="!allowNewServer"
                (click)="onCreateServer()">Add Server</button>
            <!-- <p [innerText]="allowNewServer"></p> -->
            <p>{{serverCreationStatus}}</p>
            <app-server></app-server>
            <app-server></app-server>
            
    FILE: servers.component.ts      
              import { Component, OnInit } from '@angular/core';

          @Component({
            // selector: '[app-servers]',
           selector: 'app-servers',
            // template: `
            // <app-server></app-server>
            // <app-server></app-server>`,
            templateUrl: './servers.component.html',
            styleUrls: ['./servers.component.css']
          })
          export class ServersComponent implements OnInit {
            allowNewServer = false;
            serverCreationStatus = 'No server was created!';
            serverName="";
            constructor() {
              setTimeout(() => {
                this.allowNewServer = true;
              },2000);

             }

            ngOnInit(): void {
            }
          onCreateServer(){
            this.serverCreationStatus = 'server was created!';
          }
          onUpdateServerName(event: any){
            // console.log(event);
            this.serverName=(<HTMLInputElement>event.target).value;
          }
          }

          Important: FormsModule is Required for Two-Way-Binding!
          Important: For Two-Way-Binding (covered in the next lecture) to work, you need to enable the ngModel  directive. This is done by adding the FormsModule  to the imports[]  array in the AppModule.

          You then also need to add the import from @angular/forms  in the app.module.ts file:

          import { FormsModule } from '@angular/forms';
          
 **Two way data binding**       
 
      FILE: app.module.ts
          import { FormsModule} from '@angular/forms';
          
          imports: [
            BrowserModule,
            FormsModule,
          ],
          
      FILE: servers.component.html
      
                    <!-- <input 
              type="text" 
              class="form-control"
              (input) = "onUpdateServerName($event)"> -->
              <input 
              type="text" 
              class="form-control"
              [(ngModel)]="serverName">
              
      FILE: servers.component.ts      
              serverName="TestServer";
              
# Directives


