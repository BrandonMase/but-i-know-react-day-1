# But I know React - Day 1

### What is Angular?
Angular is an open-source front-end framework made by the Angular team at Google. Angular focuses on creating single page applications (SPA) much like Reactjs and Vuejs.

<details>
  <summary>Angular 2-6 differs from Angular 1 (Angular.js) </summary>

  Angular 2 (or just Angular) was a complete re-write of Angular 1 and had many differences in the general architecture design of the framework. Each successive update to Angular 2 used the terms Angular 3, Angular 4, etc. Angular 1 stops active development on June 30, 2018 and will be deprecated June 30, 2021. The Angular team is supporting Angular 2+ for the foreseeable future.

</details>

### Downloading the Angular CLI
The angular CLI makes creating angular applications easier by downloading all of the dependices angular needs and creating a inital project structure for you (Much like create-react-app does.) In git bash type ```npm install -g @angular/cli```. Now that you've got cli for angular you can use ```ng new my-app-name-here``` to make a new angular app. You can ```cd``` into the folder ```cd my-app-name-here``` and use ```ng serve``` to load up the angular app into the browser (just like ```npm / yarn start```). ```ng serve``` is loaded up on localhost:4200 as apposed to localhost:3000 from ```npm / yarn start```.

##### Quick note about Angular vs React

  ###### Typescript 
Angular uses Typescript instead of regular Javascript. Typescript is a superset of Javascript that lets you "type check" variables/functions/etc. You can use it to make sure a variable is what it is supposed to be (string/number/function/etc). Typescript just gives you extra features that Javascript doesn't have. It makes writing code less buggy because it will run an extra check before compiling the typescript into javascript.

  ###### No Virtual DOM
Angular doesn't have a virtual DOM like React does. It directly manipulates the DOM so libraries like Bootstrap and JQuery work right out of the box with Angular.


#### What is ```ng generate```?
ng generate will automatically add a folder with all of the common files that you need with that component/service/etc. When you use ```ng generate component component-name-here``` or ```ng g c component-name-here```, you get 4 different files. 

* ***component-name-here***.component.ts. This is the functionality of the component. Angular, by design, keeps the functionality and style separte.
* ***component-name-here***.component.spec.ts. This is the file that is used for testing the functionality of your component. You can use ```spec=false``` in the ```ng generate``` to have angular not generate this file.
* ***component-name-here***.component.css. This is the styling of your component. Obviously.
* ***component-name-here***.component.html. This is the html that is displayed for the component.

## TASK 1 - Started from the bottom now we here.
Create a new Angular app called hello-world then start the app and open up your code. Yes we are doing hello world.

<details>
  <summary>Detailed Instructions</summary>

  1. ```cd``` into a folder where you want the app to be.
  2. type ```ng new hello-world```. This generates the new angular app called hello-world for us.
  3. type ```cd hello-world```.
  4. type ```ng serve```. This starts the development server for us.
  5. Open up localhost:4200 in your browser and open your code in your code editor.
</details>

---

## TASK 2
Make the app component have an h2 tag display hello world!.

<details>
<summary>Detailed Instructions</summary>

  1. Go into the app.component.html file.
  2. Delete everything in the file.
  3. Add a ```<h2>hello world!</h2>```.
</details>

<details>
<summary>Solution</summary>

<details>
<summary> <code>app.component.html</code></summary>

```html
<h2>hello world!</h2>
```
</details>
</details>

---

## TASK 3
Make a h3 tag display hello world again! using interpolation underneath the h2 tag.

<details>
<summary>Detailed Instructions</summary>

  1. Go into the app.component.ts file.  
  2. Make a new varible called helloWorld in the AppComponent function and set it equal to hello world again!.
  ```js
  helloWorld = 'hello world again!';
  ```
  3. Go into the app.component.html file.
  4. Add ```<h3>{{ helloWorld }}</h3>``` underneath the h2 tag.
</details>

<details>
<summary>Solution</summary>
  <details>
  <summary><code>app.component.html</code></summary>

```html
<h2>hello world!</h2>
<h3>{{ helloWorld }}</h3>
```
</details>

<details>
<summary><code>app.component.ts</code></summary>

```js
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  helloWorld = 'hello world again!';
}

```
</details>

</details>

---
## TASK 4
Displaying hello world again! isn't that interesting. Make an input that changes that what is displayed in the h3 tag.

---
##### A word about ngModel and what it is like in React.

  Using **[(ngModel)]** (more specifically the [()]) is the way to tell Angular that we are going to use two way data binding. This is like saying
   ```js
  <input value={this.state.helloWorld} onChange={(e) => this.setState({helloWorld:e.target.value})}>
  ```
  in React. It tells Angular that we want to initially use the helloWorld variable as the value of the input but, we also want the user to be able to change the the input AND change the helloWorld variable at the same time.

---

<details>
<summary>Detailed Instructions</summary>

  1. First we need to import the FormsModule from Angular. Go to ```app.module.ts``` and ```import { FormsModule } from '@angular/core'``` 
  2. Add FormsModule to the import in @NgModule.
  2. Go to the ```app.component.html``` file and add ```<input type="text" [(ngModel)]="helloWorld">``` above the h2 tag.

</details>

<details>
<summary>Solution</summary>
  <details>
  <summary><code>app.module.ts</code></summary>

```js
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
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

```
</details>

<details>
<summary><code>app.component.html</code></summary>

```js
<h2>hello world!</h2>
<input type="text" [(ngModel)]="helloWorld">
<h3>{{ helloWorld }}</h3>
```
</details>

</details>



