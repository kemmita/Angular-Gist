1. html
```html
<div class="row">
    <div class="col-xs-12">
      <p>Add new Servers or blueprints!</p>
      <label>Server Name</label>
      //define a local ref using the # symbol
      <input type="text" class="form-control" #serverName>
      <label>Server Content</label>
      <input type="text" class="form-control" #serverContent>
      <br>
      <button
        class="btn btn-primary"
        (click)="onAddServer(serverName, serverContent)">Add Server</button>
      <button
        class="btn btn-primary"
        (click)="onAddBlueprint(serverName, serverContent)">Add Server Blueprint</button>
    </div>
  </div>
```
2. ts
```ts
import { Component, OnInit, EventEmitter, Output, ViewChild, ElementRef } from '@angular/core';

@Component({
  selector: 'app-cockpit',
  templateUrl: './cockpit.component.html',
  styleUrls: ['./cockpit.component.css']
})
export class CockpitComponent implements OnInit {
  @Output() public serverCreated = new EventEmitter<{serverName: string, serverContent: string}>();
  @Output() public blueprintCreated = new EventEmitter<{blueprintName: string, blueprintContent: string}>();;
  
  // With @ViewChild we will gain access to the local refs
  @ViewChild('serverContent', {static: true}) public serverContent: ElementRef;
  @ViewChild('serverName', {static: true}) public serverName: ElementRef;
  constructor() { }

  ngOnInit(): void {
  }

  onAddServer() { 
    // below we use the viewchilds declared above to asign the values contained within the references on this click event.
    this.serverCreated.emit({serverName: this.serverName.nativeElement.value, serverContent: this.serverContent.nativeElement.value});
  }

  onAddBlueprint() {
    this.blueprintCreated.emit({blueprintName: this.serverName.nativeElement.value, blueprintContent: this.serverContent.nativeElement.value});
  }
}

```
