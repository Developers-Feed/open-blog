---
title: "React component to add traffic sign in leaflet map"
datePublished: Sat Aug 19 2023 00:45:00 GMT+0000 (Coordinated Universal Time)
cuid: cllhjcjjh03pspmnvcme75jhm
slug: react-component-to-add-traffic-sign-in-leaflet-map
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692420293112/3c07629d-e1e5-4ed8-a61e-fc1d8ae1caf9.jpeg

---

---
title: React component to add traffic sign in leaflet map
published: true
date: 2023-08-19 00:45:00 UTC
tags: Maps,Leaflet,Reactleaflet
canonical_url: https://reactjsexample.com/react-component-to-add-traffic-sign-in-leaflet-map/
---

# React Leaflet Traffic Sign
 ![React component to add traffic sign in leaflet map](https://cdn.hashnode.com/res/hashnode/image/upload/v1692420293112/3c07629d-e1e5-4ed8-a61e-fc1d8ae1caf9.jpeg)

React component to add traffic sign in leaflet.

[![React component to add traffic sign in leaflet map](https://cdn.hashnode.com/res/hashnode/image/upload/v1692420295079/b1b472ff-5ab4-4d59-81ff-adffaff6119c.gif)](https://camo.githubusercontent.com/cd177f4afb37ee1fc1cf05d02fb2c69dac2063f251eb668c3dae238b91166b27/68747470733a2f2f692e6962622e636f2f4b6a5458764a322f52656163742d4c6561666c65742d547261666669632d5369676e2e676966)

## Getting Started

```
import { ReactLeafletTrafficSign } from "ReactLeafletTrafficSign";

<ReactLeafletTrafficSign 
   position={ route[0] } 
   image="/overspeed.png" 
   title="Speed Traffic Sign"
   data={{
      fuel: 5.5,
      speed: 100,
      odometer: 10000,
      dateTime: new Date("2024-02-01T05:48:000Z")
      location: [-23.45678, 54.3210]
   }}
   height={ 24 } 
   width={ 24 }/>
```

## Example

```
import { MapContainer, TileLayer } from "react-leaflet";
import { ReactLeafletTrafficSign } from "ReactLeafletTrafficSign";

const Example = function() {

   const route = [[0,0], [1,1], [2,2] ];

   return(
      <MapContainer center={ [0,0] } zoom={ 0 }>

         <TileLayer url="http://tile.com/map"/>

         <Polyline positions={ route } pathOptions={{ color: "#000000", weight: 5 }}/>
         
         <ReactLeafletTrafficSign 
            position={ route[0] } 
            image="/alert.png" 
            title="Alert Traffic Sign"
            data={{
               fuel: 8.2,
               speed: 80,
               odometer: 50000,
               dateTime: new Date("2024-05-02T14:48:500Z")
               location: [-23.45678, 54.3210]
            }}
            height={ 24 } 
            width={ 24 }/> 

      </MapContainer>
   );

};

export default Example;
```

## Props

**ReactLeafletTrafficSignProps**

| name | type | description |
| --- | --- | --- |
| position | LatLngExpression | Marker position in the map |
| image | string | Marker URL or Source Image |
| title | string | Title of the Marker |
| datas | Object | Datas to description Marker basead key and value |
| height | number | Marker height size |
| width | number | Marker width size |
| anchorHeight? | number | Optional\* Marker anchor in height |
| anchorWidth? | number | Optional\* Marker anchor in width |
| offsetHeight? | number | Optional\* The offset size marker in height |
| offsetWidth? | number | Optional\* The offset size marker in width |

**Examples Props**

```
// Leaflet Latitude and Longitude Expression
const position = [-12.3456, 87.6543] as L.LatLngExpression;

// datas: { [key: string]: string }
const datas = {
   address: "Havelchaussee, 14193 Berlin, Germany",
   position: "52.488192, 13.203841",
   timestamp: "2023-11-08",
};
```

## License

MIT License.

## GitHub

[View Github](https://github.com/pdaug/react-leaflet-traffic-sign?ref=reactjsexample.com)