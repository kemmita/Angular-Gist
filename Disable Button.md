1. In your ts file create a boolean.
```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-servers',
  templateUrl: './servers.component.html',
  styleUrls: ['./servers.component.css']
})
export class ServersComponent implements OnInit {
  public allowNewServer: boolean = false;

  constructor() { 
  }

  ngOnInit(): void {
  }

}
```
2. In the html file, use prop binding
```html
<div class="container">
    <button class="btn btn-primary" [disabled]='allowNewServer'>Add Server</button>
    <app-server></app-server>
</div>
```
