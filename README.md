### ng-basic-routes simple angular app

#### Step-by-step

- Generate 3 sample component (Home, About, Contact)

  ```
  $> ng generate component Home
  $> ng generate component About
  $> ng generate component Contact
  ```

- Import routes class type and router module in `app.module.ts`

  ```js
  import { RouterModule, Routes } from "@angular/router";
  ```

- Register routes

  ```js
  import { RouterModule, Routes } from "@angular/router";

  const routes: Routes = [
    { path: "", redirectTo: "home", pathMatch: "full" },
    { path: "home", component: HomeComponent },
    { path: "about", component: AboutComponent },
    { path: "contact", component: ContactComponent }
  ];
  ```

- Then add the registered routes to import section also with the providers.

  ```js
  @NgModule({
  declarations: [AppComponent, HomeComponent, AboutComponent, ContactComponent],
  imports: [BrowserModule, AppRoutingModule, RouterModule.forRoot(routes)],
  providers: [
    {
      provide: APP_BASE_HREF,
      useValue: "/"
    }
  ],
  bootstrap: [AppComponent]
  })
  ```

- Add navigation link

  ```html
  <ul>
    <li><a [routerLink]="['/home']">Home</a></li>
    <li><a [routerLink]="['/about']">About us</a></li>
    <li><a [routerLink]="['/contact']">Contact Us</a></li>
  </ul>
  ```

- Then add `<router-outlet>` tag. This tag is responsible to specify where the rendered component was render.

  ```html
  <h4>ng-basic-routes app</h4>
  <ul>
    <li><a [routerLink]="['/home']">Home</a></li>
    <li><a [routerLink]="['/about']">About us</a></li>
    <li><a [routerLink]="['/contact']">Contact Us</a></li>
  </ul>

  <router-outlet></router-outlet>
  ```

#### Deployment

[https://ng-basic-routes.philiplambok.now.sh](https://ng-basic-routes.philiplambok.now.sh)
