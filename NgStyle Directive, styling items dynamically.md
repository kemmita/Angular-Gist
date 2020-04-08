1. Ts file
```ts
import { Component, OnInit, Input } from '@angular/core';

@Component({
  selector: 'app-server',
  templateUrl: './server.component.html',
  styleUrls: ['./server.component.css']
})
export class ServerComponent implements OnInit {
  public servers: object[] = [
    {
      serverName: 'Server One',
      serverStatus: 'active'
    },
    {
      serverName: 'Server Two',
      serverStatus: 'inactive'
    }
  ]

  constructor() { }

  ngOnInit(): void {

  }

  getColor(serverStatus: string){
    return serverStatus === 'active' ? 'green' : 'red';
  }

}
```
2. Html file
```html
<p *ngFor='let server of servers' [ngStyle]="{backgroundColor: getColor(server.serverStatus)}">{{server.serverName}}</p>
```
