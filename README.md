# 3d-threejs
This portfolio website with Vite.js. Developed with Vanilla JS and Three.js.

And the special in this case is an **animated 3d scrolling animation**. 

It is a simple application that explore many computer graphics concepts.

## Install Dependecies
Run `npm install`

## Development server

Run `npm run dev` for s dev server. Navigate to `http://localhost:300`. The app will automatically reload if you change any of the source files

## Example

![demonstrativo](https://github.com/brunacypriano/3d-threejs/blob/master/demonstrativo.gif)

## Snippet

Some of the most visually impressive websites use scroll animations with Three.js. The following snippet is configures a Three.js scene to animate when the user moves the scrollbar.

### Scene

Setup a basic fullscreen using the example from the official docs:

~~~javascript
impot * as THREE from 'three';

const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

const renderer = new THREE.WebGLRenderer();
renderer.setSize( window.innerWidth, window.innerHeight );
document.body.appendChild( renderer.domElement );

~~~

Make the canvas stay fixed to screen as an animated background.

~~~css
  canvas {
    position: fixed;
    top: 0;
    left: 0;
  }
~~~

### Overlaying Content

Overlay the main content with abosolute positioning. It is given an artifically large height value to make it scroll without content.

~~~css 
main {
    width: 100vw;
    height: 500vh;
    z-index: 99;
    position: absolute;
  }
  ~~~
  ~~~html
<body>
    <main></main>
</body>
~~~

### Animate on Scroll
Finally, add a cube to the scene and animate it. Listen to the `onscroll` on the body to trigger a change or calculate the next animation position.

~~~javascript
const geometry = new THREE.BoxGeometry();
const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
const cube = new THREE.Mesh( geometry, material );
scene.add( cube );

camera.position.z = 5;

function animate() {
  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;
  cube.rotation.z += 0.01;

  renderer.render( scene, camera );
}

document.body.onscroll = () => { 
  animate()
  console.log(document.body.offsetTop)
}
~~~

#### Have questions?

Send me an email: cyprianopartner@gmail.com
  
