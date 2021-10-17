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



















