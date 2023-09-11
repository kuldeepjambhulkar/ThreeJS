# ThreeJS Learnings

Day #1  
**Progress as of now 👇**
- able to create a basic setup of threeJS.
- able to add camera controls, box, axesHelpers in the scene.


**Create renderer 👇**
```javascript
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);
```
**Create camera & scene👇**
```javascript
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
```

**Render scene 👇**
```javascript
    renderer.render(scene, camera);
```

**Add an axis helper in the scene 👇**
```javascript
    const axesHelper = new THREE.AxesHelper(5);
    scene.add(axesHelper);
    camera.position.z = 10;
    camera.position.y = 2;

    camera.position.set(0, 2, 5);
```

**Add a box in the scene 👇**
```javascript
const boxGeometry = new THREE.BoxGeometry();
const boxMaterial = new THREE.MeshBasicMaterial({color: 0x00ff00});
const box = new THREE.Mesh(boxGeometry, boxMaterial);
scene.add(box);
```
**Animate the box 👇**
```javascript
function animate(){
    box.rotation.x += 0.01;
    box.rotation.y -= 0.05;
    renderer.render(scene, camera);
}

renderer.setAnimationLoop(animate);
```


**Adding mouse controls to the scene 👇**
```javascript
import {OrbitControls} from 'three/examples/jsm/controls/OrbitControls';
const orbit = new OrbitControls(camera, renderer.domElement);

// update the orbit after every time you set the camera postion
orbit.update();
```