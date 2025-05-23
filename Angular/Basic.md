##      Basic Angular

Components
●	Template -> html/css
●	Class -> like starting form export/import class
●	Metadata -> Decorator ( like starting form @component,@injector)

## Interpolation
Assign a Variable and Call by curly bracket

TestName = ‘Amit’;

Call in html
<p>  {{TestName}}  </p>


** it’s also able to call Function, arithmetic operation etc


## Property Binding

Calling a variable or class form ts file using [] (square bracket) like interpolation
But interpolation only use string

varColor=’red’;


<p [id]=”varColor” > test 0 </p>

Class Binding

<div [class.class1]="ConditionerVariable"> test 1</div>
<div [ngClass]="ConditionerClassName"> test 2</div>

 In ts
ConditionerVariable=false;
ConditionerClassName={
   classFontStyle :true,
   classTextColor :true,
   classFontSize :false
 };

 In css
.class1{
   color:red;
}
.classFontStyle{
   font-style: italic;
}
.classTextColor{
   color:blueviolet;
}
.classFontSize{
   font-size: 20px;
}

## Style Binding

<div [style.color]="'green'"> test 3</div>
<div [style.backgroundColor]="'green'"> test 4</div>
<div [ngStyle]="ConditionStyle"> test 5</div>

In ts

ConditionStyle={
   color:'blue',
   //fontStyle:'italic',
   'Font-style':'italic',
};

<p  [style.BackgroungColor]=”varColor” > Test       </p>

It’s taking value from assign Variable VarColor


Two Way Binding

It async Data from ts to html and vice versa 

This bracket also call Banana in bracket

In TS

testVar=”djdjjdjdjd”;

In Html
 <input [(ngModal)]=”testVar” />


Template Reference Variables

<input #myInput type=”text” />
<button (click)=”loMessage(myInput.value)”> </button>

//passing input variable input field to ts variable


## Directive

Is a html Special Attribute like *ngIf  ,*ngFor 

## ******************* ngIf *********************************#

<p *ngIF=”testVar; else elseBlock”></p>
<ng-template #elseBlock >   This Block is Hidden</ng-template>

## ******************* ngSwitch *********************************#

<div *ngSwitchCase =”’red’”> this is red color</div>
<div *ngSwitchCase =”’blue’”> this is blue color</div>

<div *ngSwitchDefault> this is default color</div>


## ******************* ngFor *********************************#


<div  *ngFor=”let color of colors”>{{color}}</div>

<div  *ngFor=”let color of colors; index as i”>{{i}}{{color}}</div>

<div  *ngFor=”let color of colors; last as l”>{{l}}{{color}}</div>
// last , first ,even ,odd alway return true and false


## Dependency Injection(DI)

●	Dependency : Depend on external source or not creating itself
●	Injection : call or create a instant in constructor
● flexible, efficient, and robust, as well as testable and maintainable
Simply calling a class using it


Call a service or class using DI

File.ts

…

constructor(public service:Service){
this.service.className();
} 


Call a service or class Without using DI

File.ts

…

constructor(){
Var var1= new Service();
var1.className();
}

### Some Angular Cli

ng build --prod --base-href http://localhost/projectName/dist/projectName/


## Routing In Angular 6

In route-module.ts

const routes: Routes = [
 {path: '',component: NewCmpComponent}, //set Default component like index.html 
 {path: 'new-cmp',component: NewCmpComponent}, //go to  component without data localhost:4200/new-cmp


 {path: 'second/:id',component: SecondComponent} ,//go to  component with data id=2
Like localhost:4200/second/2 


 {path: 'second',component: SecondComponent , children:[
   {path:'profile' , component:ProfileComponent}
 ]} , //go to  component with child
Like localhost:4200/second/profile

 {path: '**',component: SecondComponent},//go to  component if found false path wild card entry 

];


Router through html

<button routerLink="second">goToSecond</button>
<button routerLink="second/2">goToSecond</button> //with data


Router TS 


this.router.navigate(['second',{id:"am"}]); //with data
this.router.navigate(['second'}]);

Getting Data from TS
import { Router ,ActivatedRoute} from '@angular/router';
import { Location } from '@angular/common';
import { Location } from '@angular/common';


...
console.log("SecondComponent Router",this.ActivatedRoute.snapshot.paramMap.get("id"));


// to go back
GotoBack(){
   this.location.back();
 }
// set root or make home page in ionic4 or angular

this.router.navigate([pageName], {replaceUrl: true})

