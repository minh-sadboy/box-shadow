<template>
  <div>
    <canvas id="main-car"></canvas>
  </div>
</template>

<style>
#main-car {
  width: 100%;
  height: 100%;
  display: block;
  top: 0;
  left: 0;
}
</style>
<style module>
</style>


<script>
import {
  Scene,
  WebGLRenderer,
  PerspectiveCamera,
  MeshPhongMaterial,
  HemisphereLight,
  PointLight,
  CubeTextureLoader,
  PlaneGeometry,
  TextureLoader,
  RepeatWrapping,
  MeshBasicMaterial,
  Mesh,
  MixOperation,
  Vector3,
  Vector2,
  Raycaster,
  BoxGeometry,
  MeshNormalMaterial,
  Euler,
  BufferGeometry,
  LineBasicMaterial,
  setFromPoints,
  Line
} from "three";
import { GLTFLoader } from "three/examples/jsm/loaders/GLTFLoader";
import { DRACOLoader } from "three/examples/jsm/loaders/DRACOLoader";
import { DecalGeometry } from "three/examples/jsm/geometries/DecalGeometry.js";
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls";
import Stats from "three/examples/jsm/libs/stats.module.js";
import { GUI } from "three/examples/jsm/libs/dat.gui.module.js";

export default {
  data() {
    return {};
  },
  methods: {},
  mounted() {
    const intersection = {
      intersects: false,
      point: new Vector3(),
      normal: new Vector3()
    };
    const mouse = new Vector2();
    const intersects = [];
    let mesh;
    let line;

    const textureLoader = new TextureLoader();
    const decalDiffuse = textureLoader.load("icon.png");
    const decalNormal = textureLoader.load("icon.png");

    const decalMaterial = new MeshPhongMaterial({
      specular: 0x444444,
      map: decalDiffuse,
      normalMap: decalNormal,
      normalScale: new Vector2(1, 1),
      shininess: 30,
      transparent: true,
      depthTest: true,
      depthWrite: false,
      polygonOffset: true,
      polygonOffsetFactor: -4,
      wireframe: false
    });

    const decals = [];
    let mouseHelper;
    const position = new Vector3();
    const orientation = new Euler();
    const size = new Vector3(10, 10, 10);

    const params = {
      minScale: 10,
      maxScale: 20,
      rotate: true,
      clear: function() {
        removeDecals();
      }
    };

    var theModel;
    var that = this;
    const MODEL_PATH = "model/car7Draco.gltf";

    const scene = new Scene();
    const canvas = document.getElementById("main-car");
    const renderer = new WebGLRenderer({
      canvas,
      antialias: true
    });

    document.body.appendChild(renderer.domElement);

    const cameraFar = 5;
    var camera = new PerspectiveCamera(
      50,
      window.innerWidth / window.innerHeight,
      0.1,
      1000
    );
    camera.position.z = cameraFar;
    camera.position.x = 0;
    scene.rotation.y = -Math.PI / 4;

    const geometry = new BufferGeometry();
    geometry.setFromPoints([new Vector3(), new Vector3()]);

    line = new Line(geometry, new LineBasicMaterial());
    scene.add(line);

    // load model
    var loader = new GLTFLoader();

    const dracoLoader = new DRACOLoader();
    dracoLoader.setDecoderPath("./draco/");
    loader.setDRACOLoader(dracoLoader);

    loader.load(
      MODEL_PATH,
      function(gltf) {
        mesh = gltf.scene.children[9];
        console.log(mesh);
        theModel = gltf.scene;
        that.model = theModel;
        theModel.position.y = -1;
        // theModel.scale.set(0.02,0.02,0.02);
        scene.add(theModel);
        that.load = false;
      },
      undefined,
      function(error) {
        console.error(error);
      }
    );

    var hemiLight = new HemisphereLight(0xffffff, 0xffffff, 0.64);
    hemiLight.position.set(0, 10, 0);
    scene.add(hemiLight);

    var controls = new OrbitControls(camera, renderer.domElement);
    controls.minDistance = 4;
    controls.maxDistance = 7;
    controls.maxPolarAngle = Math.PI / 2;
    controls.minPolarAngle = Math.PI / 3;
    controls.enableDamping = true;
    controls.enablePan = false;
    controls.dampingFactor = 0.1;
    controls.autoRotate = false;
    controls.autoRotateSpeed = 0.1;

    var raycaster = new Raycaster();

    mouseHelper = new Mesh(new BoxGeometry(1, 1, 10), new MeshNormalMaterial());
    mouseHelper.visible = false;
    scene.add(mouseHelper);

    let moved = false;

    controls.addEventListener("change", function() {
      moved = true;
    });

    window.addEventListener("pointerdown", function() {
      moved = false;
    });

    window.addEventListener("pointerup", function(event) {
      if (moved === false) {
        checkIntersection(event.clientX, event.clientY);
        if (intersection.intersects) shoot();
      }
    });

    window.addEventListener("pointermove", onPointerMove);

    function onPointerMove(event) {
      if (event.isPrimary) {
        checkIntersection(event.clientX, event.clientY);
      }
    }

    function checkIntersection(x, y) {
      if (mesh === undefined) return;

      console.log(mesh);

      mouse.x = (x / window.innerWidth) * 2 - 1;
      mouse.y = -(y / window.innerHeight) * 2 + 1;

      raycaster.setFromCamera(mouse, camera);
      raycaster.intersectObject(mesh, false, intersects);

      if (intersects.length > 0) {
        const p = intersects[0].point;
        mouseHelper.position.copy(p);
        intersection.point.copy(p);

        const n = intersects[0].face.normal.clone();
        n.transformDirection(mesh.matrixWorld);
        n.multiplyScalar(10);
        n.add(intersects[0].point);

        intersection.normal.copy(intersects[0].face.normal);
        mouseHelper.lookAt(n);

        const positions = line.geometry.attributes.position;
        positions.setXYZ(0, p.x, p.y, p.z);
        positions.setXYZ(1, n.x, n.y, n.z);
        positions.needsUpdate = true;

        intersection.intersects = true;

        intersects.length = 0;
      } else {
        intersection.intersects = false;
      }
    }
    const gui = new GUI();

    gui.add(params, "minScale", 1, 30);
    gui.add(params, "maxScale", 1, 30);
    gui.add(params, "rotate");
    gui.add(params, "clear");
    gui.open();
    // fps
    var stats = new Stats();
    document.body.appendChild(stats.dom);
    function animate() {
      controls.update();
      renderer.render(scene, camera);
      requestAnimationFrame(animate);

      if (resizeRendererToDisplaySize(renderer)) {
        const canvas = renderer.domElement;
        camera.aspect = canvas.clientWidth / canvas.clientHeight;
        camera.updateProjectionMatrix();
      }
      stats.update();
    }

    animate();

    function resizeRendererToDisplaySize(renderer) {
      const canvas = renderer.domElement;
      var width = window.innerWidth;
      var height = window.innerHeight;
      var canvasPixelWidth = canvas.width / window.devicePixelRatio;
      var canvasPixelHeight = canvas.height / window.devicePixelRatio;

      const needResize =
        canvasPixelWidth !== width || canvasPixelHeight !== height;
      if (needResize) {
        renderer.setSize(width, height, false);
      }
      return needResize;
    }

    function shoot() {
      console.log(intersection.point);
      position.copy(intersection.point);
      orientation.copy(mouseHelper.rotation);

      if (params.rotate) orientation.z = Math.random() * 2 * Math.PI;

      const scale =
        params.minScale + Math.random() * (params.maxScale - params.minScale);
      size.set(scale, scale, scale);

      const material = decalMaterial.clone();
      material.color.setHex(Math.random() * 0xffffff);

      const m = new Mesh(
        new DecalGeometry(mesh, position, orientation, size),
        material
      );

      decals.push(m);
      scene.add(m);
    }

    function removeDecals() {
      decals.forEach(function(d) {
        scene.remove(d);
      });

      decals.length = 0;
    }
  }
};
</script>
