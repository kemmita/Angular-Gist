1. HTML
```html
<div class="row">
    <div class="col-xs-12">
      <p>Add new Servers or blueprints!</p>
      <label>Server Name</label>
      //create the reference to the input element below "#serverName"
      <input type="text" class="form-control" #serverName>
      <label>Server Content</label>
      <input type="text" class="form-control" #serverContent>
      <br>
      <button
        class="btn btn-primary"
        //pas the reference to the method as so
        (click)="onAddServer(serverName, serverContent)">Add Server</button>
      <button
        class="btn btn-primary"
        (click)="onAddBlueprint(serverName, serverContent)">Add Server Blueprint</button>
    </div>
  </div>
```
2. ts
```ts
import { Component, OnInit, EventEmitter, Output } from '@angular/core';

@Component({
  selector: 'app-cockpit',
  templateUrl: './cockpit.component.html',
  styleUrls: ['./cockpit.component.css']
})
export class CockpitComponent implements OnInit {
  @Output() public serverCreated = new EventEmitter<{serverName: string, serverContent: string}>();
  @Output() public blueprintCreated = new EventEmitter<{blueprintName: string, blueprintContent: string}>();;

  constructor() { }

  ngOnInit(): void {
  }
  
  //pass the props as HTMLInputElement(s)
  onAddServer(serverName: HTMLInputElement, serverContent: HTMLInputElement) { 
    this.serverCreated.emit({serverName: serverName.value, serverContent: serverContent.value});
  }
  
  onAddBlueprint(serverName: HTMLInputElement, serverContent: HTMLInputElement) {
    this.blueprintCreated.emit({blueprintName: serverName.value, blueprintContent: serverContent.value});
  }
}

```
