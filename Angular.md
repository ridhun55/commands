# Install Angular CLI Globally
```shell
npm install -g @angular/cli
```
# Angular Version
```shell
ng version
```
# Angular Help
```shell
ng help
```
# Create Angular Project
```shell
ng new my-project
```
Run Angular Project
```shell
cd my-project
```
```shell
ng serve
```

# File & Folder Structure
<pre>

package.json
node_modules
src 
  |-- apps
  |-- assets
  |-- environments
  |-- index.html
  |-- main.js
  |-- style.css

</pre>
# Interpolation & Values
1. In "app.component.ts"
```shell
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'my-project';
  data = "example data"
  getVal(){
    return "function returned value"
  }
}

```
2. In "app.component.html"
```shell
<h1>Hello ! {{ title }}</h1>
<h1>data :  {{ data }}</h1>
<h1>sum :  {{ 1+2+3 }}</h1>
<h1>{{ getVal() }}</h1>
```

# Create Angular Component
```shell
ng generate component header
```
or [ in short ]
```shell
ng g c header
``` 
add "&lt;app-header	&gt;&lt;/app-header	&gt;" inside "app.component.html"

================== Inline-style & Inline-template =================================

# Create component with Inline-style 
```shell
ng g c footer --inline-style
```
<pre>
it generate only 3 files, they are

|-- footer.component.html 
|-- footer.component.spec.ts 
|-- footer.component.ts 
</pre>
add "&lt;app-footer&gt;&lt;/app-footer&gt;" inside "app.component.html"

1. add class in footer.component.html
```shell
<h1 class="text-red">footer works!</h1>
```
2. write style in "footer.component.ts" inside 'backtick'
```shell
@Component({
  selector: 'app-footer',
  templateUrl: './footer.component.html',
  styles: [
    `.text-red{
      color:red;
    }`
  ]
})
```

# Create component with Inline-template 
```shell
ng g c footer --inline-template
```
add "&lt;app-students&gt;&lt;/app-students&gt;" inside "app.component.html"
1. add class in "template" inside students.component.html
```shell
@Component({
  selector: 'app-students',
  template: `
    <h2 class="text-red">
      students works!
    </h2>
  `,
  styleUrls: ['./students.component.css']
})
```
2. write css for that class inside students.component.css
```shell
.text-red{
   color: blue;
}
```

# Create component with Inline-style & Inline-template 
```shell
ng g c user --inline-style --inline-template
```
<pre>
it generate only 2 files, they are

|-- user.component.spec.ts 
|-- user.component.ts 
</pre>
add "&lt;app-user&gt;&lt;/app-user&gt;" inside "app.component.html"

1. add "style" and "template" inside user.component.html
```shell
@Component({
  selector: 'app-user',
  template: `
    <h1 class="text-yellow">
      user works!
    </h1>
  `,
  styles: [
    `.text-yellow{
      color:yellow;
    }`
  ]
})
```

========== module ==========================================================
<pre>
Concept Of Module

module_1
  |-- component_1
  |-- component_2
  |-- component_3
  |-- component_4
  
module_2
  |-- component_1
  |-- component_2
  |-- component_3
  |-- component_4
</pre>

# Create Module
```shell
ng generate module user-auth
```
1. register module into the "app.module.ts" file [ import & register]
```shell
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';
import { UserAuthModule } from './user-auth/user-auth.module';    // <-------

@NgModule({
  declarations: [
    AppComponent,
  ],
  imports: [
    BrowserModule,
    UserAuthModule              // <-------
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

2. Component create inside the user-auth module
```shell
ng generate component user-auth/login
```
3. exports that Component from "user-auth.module.ts"
```shell
@NgModule({
  declarations: [
    LoginComponent
  ],
  imports: [
    CommonModule
  ],
  exports: [                // <-------
    LoginComponent
  ]
})
```



========== Function =====================

# Button Click [function with no parameters]
1. Create a fuction in "app.component.js"
```shell
export class AppComponent {
  title = 'my-project';
  getName(){
    alert("Button Clicked")
  }
}
```
2. add a button with click event in "app.component.html"
```shell
<button (click)="getName()">Click Me</button>
```

# Button Click [function with parameters]
1. fuction pass a parameter in "app.component.html"
```shell
<button (click)="getName('Ridhun')">Click Me</button>
```
2. Create a fuction with parameter in "app.component.js"
```shell
export class AppComponent {
  title = 'my-project';
  
  getName(name:string){
    alert("parameter is : " + name)
  }
}

```
<pre>
Function Parameters
name : string   <-- function for string
name : number   <-- function for number
name: string | number   <-- function for string or number

<button (click)="getName('Ridhun')">Click Me</button>   <-- for string
<button (click)="getName(100)">Click Me</button>   <-- for number
</pre>

NOTE : make "String":"false" in "ts.config.js" file. it will allow function parameters "any". then use
<pre>
getName(name){
    alert("parameter is : " + name)
  }
</pre>


========== Events =====================

# Basic Events 
<pre>
1. click
2. keyup
3. keydown
4. blur
5. input

6. mouseover
7. mouseleave
</pre>

2. Create a fuction with parameter in "app.component.js"
```shell
export class AppComponent {
  title = 'my-project';
  
  getData(val:string){    //  <----- 
    console.warn(val)
  }
}
```
2. related Events in "app.component.html"
```shell
<button #box1 (click)="getData('click event')">Click Me</button>
<br>
<br>
<input #box2 (keyup)="getData(box2.value)" placeholder="keyup input"/>
<br>
<br>
<input #box3 (keydown)="getData(box3.value)" placeholder="keydown input"/>
<br>
<br>
<input #box4 (blur)="getData(box4.value)" placeholder="blur input"/>
<br>
<br>
<input #box5 (input)="getData(box5.value)" placeholder="input event"/>

<h1 (mouseover)="getData('MouserOvered')">Mouse Over Event</h1>
<h1 (mouseleave)="getData('MouserLeaved')">Mouse Leave Event</h1>
```

=============================================

# Get Input TextBox Value & Print

```shell
1. In "app.component.html"

  <input #id_1 (keyup)="getInputValue(id_1.value)" />
  <p>{{ printVar }}</p>

2. In "app.component.ts"

  export class AppComponent 
  {
    printVar = '';

    getInputValue(data:string)
    {
      this.printVar = data;
  }
```

# Get Input TextBox Value & Print with Button Click

```shell
1. In "app.component.html"

  <input #id_1 />
  <button (click)="getInputValue(id_1.value)">Print value</button>

  <p>{{ printVar }}</p>

2. In "app.component.ts"

  export class AppComponent 
  {
    printVar = '';

    getInputValue(data:string)
    {
      this.printVar = data;
  }
```

# Up Down Counter

```shell
1. In "app.component.html"

  <button #btn1 (click)="countFun('up')">Increment</button>
  <p>Count : {{ count }}</p>
  <button #btn2 (click)="countFun('down')">Decrement</button> 

2. In "app.component.ts"

  export class AppComponent {

  count = 0;
  countFun(c_type:string)
  {
    if(c_type==='up')
    {
      this.count = this.count + 1
    }
    else if(c_type==='down')
    {
      this.count = this.count - 1
    }
    
  }
}
```

# If Else Condition

```shell
1. In "app.component.ts"

  export class AppComponent {
  flag = true;
  }
  
2. In "app.component.html"

  <h1 *ngIf="flag; then Block1 else Block2"></h1>

  <ng-template #Block1>
     <h1>If condition section</h1>
  </ng-template>

  <ng-template #Block2>
     <h1>Else condition section</h1>
  </ng-template>
```

```shell
1. In "app.component.ts"

  export class AppComponent {
  flag = "yes";
  }
  
2. In "app.component.html"

  <h1 *ngIf="flag=='yes'; then Block1 else Block2"></h1>

  <ng-template #Block1>
     <h1>If condition section</h1>
  </ng-template>

  <ng-template #Block2>
     <h1>Else condition section</h1>
  </ng-template>
```
# Multiple If Else Condition
```shell
1. In "app.component.ts"

  export class AppComponent {
  color = "red";
  }
  
2. In "app.component.html"

  <ng-template [ngIf]="color === 'red'">
     <h1 style="color:red"> Red color </h1>
  </ng-template>

  <ng-template [ngIf]="color === 'green'">
     <h1 style="color:green"> Red Green </h1>
  </ng-template>
  
  <ng-template [ngIf]="color === 'blue'">
     <h1 style="color:blue"> Red blue </h1>
  </ng-template>
```

# Switch case
```shell
1. In "app.component.ts"

  export class AppComponent {
  op = "red";
  }
  
2. In "app.component.html"

  <div [ngSwitch]="op">
    <h1 *ngSwitchCase =" 'red' "> Red Color</h1>
    <h1 *ngSwitchCase =" 'green' "> Green Color</h1>
    <h1 *ngSwitchCase =" 'blue' "> Blue Color</h1>
    <h1 *ngSwitchDefault > Default case </h1>
  </div>
```

# For Loop
- Loop using inside html file - use angular loop
- Loop using inside ts file - use javascript loop

1.For loop inside html
```shell
1. In "app.component.ts"

  export class AppComponent {
  arr = ['red', 'blue', 'green', 'pink', 'black'];
  }
  
2. In "app.component.html"

  <h3 *ngFor = "let i of arr"> colour is : {{ i }} </h3>
```

```shell
1. In "app.component.ts"

  export class AppComponent {
    obj = [
        { label:'A', color:'red', code:'123' },
        { label:'B', color:'blue', code:'456' },
        { label:'C', color:'green', code:'789' },
        { label:'D', color:'pink', code:'987' },
        { label:'A', color:'black', code:'765' },
      ]
  }
  
2. In "app.component.html"

  <h3 *ngFor = "let item of obj"> colour is : {{ item.label }} -- {{ item.color }} -- {{ item.code }}</h3>
```

# Nested For loop 
```shell
1. In "app.component.ts"

  export class AppComponent {
    obj = [
        { label:'A', color:'red', code:'123', details:['abc', 'bca', 'cba']},
        { label:'B', color:'blue', code:'456', details:['def', 'efd', 'fed']},
        { label:'C', color:'green', code:'789', details:['ghi', 'hig', 'igh']},
        { label:'D', color:'pink', code:'987', details:['qwe', 'weq', 'ewq']},
        { label:'A', color:'black', code:'765', details:['zxc', 'xcz', 'czx']},
      ]
  }
  
2. In "app.component.html"
  
  <ul *ngFor = "let item of obj">
    <li> {{ item.label }} </li>
    <li> {{ item.color }} </li>
    <li> {{ item.code }} </li>

    <ul *ngFor = "let subitem of item.details">
      <li> {{ subitem }} </li>
    </ul>
  </ul>
  
```




