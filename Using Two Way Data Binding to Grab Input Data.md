1. Html template
```html
<div class="container">
    <label>Server Name</label>
    <!--Using ngModel we can grab the name of the serverName value entered-->
    <input type="text" class="form-control" [(ngModel)]='serverName'>
    <button class="btn btn-primary" (click)="onCreateServer()">Add Server</button>
    <p>Server Name: {{ serverName }}</p>
</div>
```
2. TS file
```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-servers',
  templateUrl: './servers.component.html',
  styleUrls: ['./servers.component.css']
})
export class ServersComponent implements OnInit {
  public serverName: string;

  constructor() { 
  }

  ngOnInit(): void {
  }

  // when this method is triggered via the button, we will grab the current value of the serverName within the input field.
  onCreateServer() {
    console.log(this.serverName);
    this.serverName = '';
  }

}
```
