# Agm-Direction

[![npm version](https://badge.fury.io/js/agm-direction.svg)](https://badge.fury.io/js/agm-direction)
[![npm](https://img.shields.io/npm/dm/localeval.svg)](https://github.com/explooosion/Agm-Direction)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
[![Dependency Status](https://david-dm.org/explooosion/Agm-Direction.svg?theme=shields.io)](https://david-dm.org/explooosion/Agm-Direction)

[Agm-Direction](https://github.com/explooosion/Agm-Direction) is the directive for [@agm/core](https://github.com/SebastianM/angular-google-maps)

+ Angular 2+
+ Google Map API 

![Agm-Direction](https://i.imgur.com/DCIoXqS.jpg)

## Installation

Installation is done using the
[`npm install` command](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

+ Install @agm/core
  ```bash
  npm install --save @agm/core
  ```

+ Install agm-direction
  ```bash
  npm install --save agm-direction
  ```

## Importing Modules

+ @agm/core
+ agm-direction

```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';

import { AgmCoreModule } from '@agm/core';            // @agm/core
import { AgmDirectionModule } from 'agm-direction';   // agm-direction

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AgmCoreModule.forRoot({ // @agm/core
      apiKey: 'your key',
    }),
    AgmDirectionModule      // agm-direction
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

## Usage

+ HTML

  ```html
  <button type="button" (click)="getDirection()">Get</button>

  <agm-map [latitude]="lat" [longitude]="lng">
    <agm-direction *ngIf="dir" [origin]="dir.origin" [destination]="dir.destination"></agm-direction>
  </agm-map>
  ```

+ CSS

  ```css
  agm-map {
      height: 400px;
  }
  ```

+ TS

  ```ts
    lat: Number = 24.799448;
    lng: Number = 120.979021;
    zoom: Number = 14;

    dir = undefined;

    getDirection() {
      this.dir = {
        origin: { lat: 24.799448, lng: 120.979021 },
        destination: { lat: 24.799524, lng: 120.975017 }
      }
    }
  ```

## Properties

+  @Input() `origin`: { lat: Number, lng: Number }
+  @Input() `destination`: { lat: Number, lng: Number }
+  @Input() `waypoints`: object = []
+  @Input() `travelMode`: string = 'DRIVING'
+  @Input() `optimizeWaypoints`: boolean = true
+  @Input() `visible`: boolean = true
+  @Input() `renderOptions`: any
+  @Input() `drivingOptions`: any = undefined;
+  @Input() `transitOptions`: any = undefined;
+  @Input() `panel`: object | undefined

## Options

#### Remove Direction

+ HTML

  ```html
  <agm-direction ... [visible]="show"></agm-direction>
  ```

+ TS

  ```ts
  this.show = false
  ```

#### Show Panel Direction

Use of the DirectionsRenderer object to display a directions [panel](https://developers.google.com/maps/documentation/javascript/examples/directions-panel?hl=zh-tw).

+ HTML

  ```html
  <agm-direction ... [panel]="myPanel"></agm-direction>
  <div #myPanel></div>
  ```

Or you could define a function using the panel:

+ HTML
  ```html
  <agm-direction ... [panel]="setPanel()"></agm-direction>
  <div id="myPanel"></div>
  ```

+ TS

  ```ts
  function setPanel(){
    return document.querySelector('#myPanel'); 
  }
  ```

#### DirectionsRendererOptions

This object defines the properties that can be set on a [DirectionsRenderer](https://developers.google.com/maps/documentation/javascript/reference#DirectionsRendererOptions) object.

+ HTML

  ```html
  <agm-direction ... [renderOptions]="options"></agm-direction>
  ```

+ TS

  ```ts
  options = {
    suppressMarkers: true,
    draggable: true,
    markerOptions: {
      icon: 'my_marker.png'
    },
    ...
  };
  ```

## Document
Less useful [document](https://robby570.tw/Agm-Direction/).

## Generator 
This library generated by [generator-angular2-library](https://github.com/jvandemo/generator-angular2-library).
