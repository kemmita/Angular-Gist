1. Services are used to keep us from writing repeat code, if we are going to need a specfic functionality throughtout our application,
we can creat and use a service inside of our desired componenets
2. create a folder called services and keep your services here
auth.services.ts 
```ts
import { Http, Headers, RequestOptions, Response } from '@angular/http';
import { Injectable } from '@angular/core';
import 'rxjs/add/operator/map';
@Injectable()
export class AuthService {
  BaseUrl = 'http://localhost:5000/api/auth';
  userToken: any;
constructor(private http: Http) {}
  login(model: any) {
    const headers = new Headers({'Content-type': 'application/json'});
    const options = new RequestOptions({headers: headers});
    return this.http.post(this.BaseUrl + 'login', model, options).map((response: Response) => {
      const user = response.json();
      if (user) {
        localStorage.setItem('token', user.tokenString);
        this.userToken = user.tokenString;
      }
    });
  }

}
```


3. now go to app.module.ts to add the service we wish to use
```ts
import { AuthService } from './_services/auth.service';



 providers: [
    AuthService
  ],
```
4.now go to the componenet and use the service
```ts
import { Component, OnInit } from '@angular/core';
import { AuthService } from '../_services/auth.service';

@Component({
  selector: 'app-nav',
  templateUrl: './nav.component.html',
  styleUrls: ['./nav.component.css']
})
export class NavComponent implements OnInit {
model: any = {};
  constructor(private authService: AuthService) { }

  ngOnInit() {
  }

  login() {
    this.authService.login(this.model).subscribe(data => {
      console.log('Alles ist gut');
    }, error => {
      console.log('Probelm');
    });
  }
}
```
