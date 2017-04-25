## I want AR

Note:
Problem, I don't have a Hololens or a Tango phone in my pocket.

---

<img src="img/phone-tablet-laptop.svg" style="height:70vh;"/>

---

### Mobile devices sensors

* Spatial and motion sensors
* Geolocation
* Camera

Note:
Ambient light, Proximity sensor and NFC

---

#### Spatial and motion sensors

Note:
Accelerometer, gyroscope and magnetometer.
Only 3DoF
SLAM: Simultaneous localization and mapping.
Sensors reconciliation.

---

#### Geolocation

<img src="img/layar-geolocation.jpg" style="height:70vh;"/>

Note:
The old Layar app with layers of geolocalised POI.
Mozilla is working on a similar DB of POI with lat, long and altitude.

---

### Camera

<img src="img/ar.svg" style="height:50vh;"/>

Note:
Use computer vision to augment the camera on the phone screen.

---

#### I need

* A phone screen <span style="color:darkorange">✓</span>
* A camera <span style="color:darkorange">✓</span>
* A computer vision library <span style="color:darkorange">✓</span>

Note:
Your mobile device already has a camera (or 2).
CV lib in JS are easy to find. Object detection.

---

#### CV lib face coordinates

* top
* left
* height
* width

---

Convert these parameters to a 3D space

---

#### x and y axes

Convert `top` and `left`

Note:
Convert canvas coordinate to Three.js (top-left / bottom/left).
Convert to (-1, 1) range.

---

#### z axis

<img src="img/z-axis.svg" style="height:50vh;"/>

Note:
Use `height` and `width` to estimate depth
Calibration needed.

---

### A-Frame
```html
<a-camera near="0.5" far="2.5"></a-camera>
```

Note:
We can deactivate position tracking as we only rely on the camera
to place objects on the scene.

---

### Three.JS
```javascript
const pos = new THREE.Vector3(x, y, z).unproject(camera);
```

Note:
Compute the center of the face (if your 3D object is centered too).
Expect values in the range of (-1, 1).

---

### Demo time

[All Saints](https://gmarty.github.io/all-saints-ar/)
