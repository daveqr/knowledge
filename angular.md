# Angular

## Quick Commands

* Generate a module

	```
	$ ng generate module <module-name>
	```

* Generate a component

	```
	$ ng generate component <module-name>/<component>
	```
	
* Generate a service

	```
	$ ng generate service services/<service>
	```	

## Routing Config

Routing configuration involves setting up a module that contains routes and importing it into the main module.

### Generate the Routing File

To generate a `categories-routing.module.ts` file and configure it for import into the `CategoriesModule`, use the following command:

```shell
$ ng generate module categories/categories-routing --flat --module=categories/categories.module
```

### Example Routing File (categories-routing.module.ts)

```
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { CategoriesHomeComponent } from './categories-home/categories-home.component';

const routes: Routes = [
  { path: '', component: CategoriesHomeComponent },
]

@NgModule({
  imports: [RouterModule.forChild(routes)],
  exports: [RouterModule],
})
export class CategoriesRoutingModule {}
```

### Example Module Using the Routing File (categories.module.ts)
```
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { CategoriesHomeComponent } from './categories-home/categories-home.component';
import { CategoriesRoutingModule } from './categories-routing.module'; // Import the routing module

@NgModule({
  declarations: [
    CategoriesHomeComponent,
  ],
  imports: [
    CommonModule,
    CategoriesRoutingModule // Import the routing module for this feature module  ]
})
export class CategoriesModule { }
```
