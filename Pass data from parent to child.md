1. Parent component.ts file contains an array of objects that we want to pass to our child component.
```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  public users = userService.GetAllUsers();
}
```
2. Parent HTML
```html
<div class="container">
  <div class="row">
    <div class="col-xs-12">
      <--loop through the users array, for each user, pass to the child component take note of the [user] this is our input property -->
      <app-user *ngFor="let user of users" [user]="user"></app-user>
    </div>
  </div>
</div>
```
3. Child TS
```ts
import { Component, OnInit, Input } from '@angular/core';

@Component({
  selector: 'app-server-element',
  templateUrl: './server-element.component.html',
  styleUrls: ['./server-element.component.css']
})
export class ServerElementComponent implements OnInit {
  // Below is the input prop that we define to pass in a user
  @Input() public user: User;
  
  constructor() { }

  ngOnInit(): void {
  }

}
```
4. Child html
```html
<div class="panel panel-default">
<div class="panel-heading">{{ user.name }}</div>
<div class="panel-body">
  <p>
    <strong>{{ user.content }}</strong>
    <em>{{ user.address }}</em>
  </p>
</div>
</div>
```
