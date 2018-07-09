# MgNg learning journey
This is a journey of learning Angular.  It is a great product and we love it!

## 2018 - Angular 6 Series
[What is new in Angular 6](#serie1)  
[A Simple Angular 6 Application](#serie2)  
[Angular 6 with Angular Material](#serie3)  
[Deploy Angular 6 App](#serie4)   
[Testing: Unit Test, Jasmine, Karma, Protractor](#serie5)  
[Using Router and Lazy Loading](#serie6)   
[What is PWA	(progressive web app)](#serie7)  
[What is RxJS](#serie8)  
[What is GSAP	(ngx-gsap-draggable?)](#serie9)  
[Using Database](#serie10)  
[Angular Universal](#serie11)  
[Under the Hood – Webpack](#serie12)  
[Under the Hood – Typescript](#serie13)  
[Under the Hood – JavaScript (Object and Function)](#serie14)  

## 1. What is new in Angular 6
---
I believe the most important is: Starting with Version 6, Angular, Material and Angular CLI will release together with the same version number.  Developers will be clear Angular, Material, and Angular CLI are compatible in the same set when they are in the same _**major version** number_ 

**Angular 6.0**, **Material 6.0** and **Angular CLI 6.0**.

I and Jeff have great interest in Angular.  We have been learning and practicing it since Angular 2.  We love to use Angular CLI, because it helps set up a good application structure to enterprise applications.

I think it is good to go through Angular 6 and discover the new features and start a series of this discovering.

## **Angular 6**
---
Angular 6 has many new features and enhancements.  This  include and not limited to those listing below:

- **Providers**: in @Injectable() decorator, a new ‘providedIn’ attribute allow us to indicate ‘root’ or any module in our application. 
``` 
Example:
@Injectable({
  providedIn: ‘root’
})
export class MyAccountService {

}
```
- **RxJS 6**: Angular 6 now uses RxJS 6 internally.
```
Example: 
import { Observable, of }  from ‘rxjs’;
import { map } from ‘rxjs/operators’;
const squares$: Observable<number>  = of(1,2).pipe(
  map(n => n * n)
)
```

For RxJS 5 or RxJS 5.5 compatible: `add rxjs-compat.`

- **Improved Service Worker Service**: Anuglar supports configuration of navigation URLs in Service Worker.  (list in ngsw-config.json).  Also safety-worker.js for deactivation of an existing service worker in production.

- **\<ng-template>**: Starting Angular 6, we should use **\<ng-template> instead of \<template>** 

- **ngModelChange**: ngModelChange is now emitted after the value is updated on its form control.

- **Better URL Serialization**: Now it is the same as query strings, some special values such as ‘(‘, ‘;’ will appear in code (%28, %29, %3B).

- **Added support for Custom Elements** (still in progress) 
- **Animations**: not need for web-animations-js
- **ElementRef\<T>**: when using @ViewChild or @ViewChildren to reference an element, we can identify it is HTMLInputElement type.
- **preserveWhitespaces**: false (by default)
- **ngModel and reactive forms**: We should use just Template-driven Forms or Reactive Forms.  Do not mix ngModel and Reactive forms.  If we have this mix in the code, we should change it to either a template-driven form or a reactive form.
```
<input [(ngModel)]=”person.lastname” [formControl]=”myCtrl”>
```
- **A new Angular renderer (Ivy)**: It compiles the templates into cleaner TypeScript code.  Then TypeScript code get transpiled into JavaScript (build time: faster, bundle size: smaller)
To use Ivy, in tsconfig.json, add:
```
“angularCompilerOptions”: {
  “enableIvy”: true
}
```
- **NgModule**: It is still in Angular 6.  In the future, we may not need NgModules as Ivy become mature. 
- **AOT code Libraries**:Easier to create and generate Libraries.
- **Runtime il8n**: This is still in progress.  It allows developer to just Load a JSON containing the translations for each locale.
- **Private properties in templates**

I learn some of these items through   
<https://auth0.com/blog/whats-new-in-angular6/>

## **Angular CLI 6** new features and useful command.
- **ng add**: to help add application features quickly, or turning application into progressive web apps.
```
example:
$ ng add @angular/material
$ ng add @angular/pwa
$ ng add @angular/elements
$ ng add @ng-bootstrap/schematics
or
$ ng add @nativescript/schematics (coming soon!)
```
- **support for libraries**: developers able to choose ng-packgr for transpiling libraries to an Angular format or use Bazel tool to build libraries.
- **ng new**: to create a new angular project (or a library)
- **ng generate**: to generate component, service, module, pipe, directive, class, …
- **ng update**: to update npm dependencies


## **Angular Material 6**
---
https://material.angular.io/guides
https://material.angular.io/components/categories
https://material.angular.io/cdk/categories

Angular Material has become easier to use in Angular 6.  Below are some important new features:

- **Tree**: to render hierarchical data and interaction pattern
- **Flexible Overlays**: it can automatically figure out a long menu and size it on the screen
- **Badge**: lightweight inline notification markers
- **Bottom-Sheet**: for mobile-specific modal interaction
- **Schematics**:
```
Example:
$ ng g @angular/material:material-nav - - name=side-nav
  
Example:
$ ng new ngMaterialProj01
**Note** in May 2018, we can add material this way after cd to the project.
$ ng add @angular/material  

But as of mid June and early July 2018.  We have to use npm or yarn to add material and cdk

**To use NPM **  
$ npm install --save @angular/material @angular/cdk  
**To use NPM **  
$ yarn add @angular/material @angular/cdk  
```
We can quickly select some starter components that fit our need.  Such as:


_@angular/material:dashboard_: Create a card-based dashboard component  

_@angular/material:table_: Create a component that displays data with a data-table 

_@angular/material:nav_: Create a component with a responsive sidenav for navigation

To use **ng generate** command to generate the starter component:
```
$ ng generate @angular/material:nav --name baseMatNav
$ ng generate @angular/material:dashboard --name baseMatDashboard
$ ng generate @angular/material:table -- name baseMatTable
```
>To findout which item you can generate through @angular/material, check it out under node_modules folder, @angular, material, schematics  
(there are rapit changes in the schematics section, make sure the names are correct, please. )

To add to your component’s html:
add:
`<baseMatNav></baseMatNav>`

To run $ ng server --open

- Reference to:
      https://medium.com/codingthesmartway-com-blog/angular-material-and-angular-6-material-design-for-angular-6b1a3ee476f0

***

# Below is a list of plan projects in this serie.  I will fill in the content and Angular application one by one.  Since it is a learning journey, each project is a special topic applys Angular 6 features; the project is not a full production application.

## 2. A Simple Angular 6 Application		
## 3. Angular 6 with Angular Material 	
## 4. Deploy Angular 6 App
## 5. Using Router and Lazy Loading		
## 6. What is PWA	(progressive web app)
## 7. What is RxJS			
## 8. What is GSAP	(ngx-gsap-draggable?)			
## 9. Using Database
## 10. Angular Universal
## 11. Under the Hood – Webpack		
## 12. Under the Hood – Typescript
## 13. Under the Hood – JavaScript (Object and Function)

