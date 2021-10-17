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
1. In app.component.ts
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
2. In app.component.html
```shell
<h1>Hello ! {{ title }}</h1>
<h1>data :  {{ data }}</h1>
<h1>sum :  {{ 1+2+3 }}</h1>
<h1>{{ getVal() }}</h1>
```

