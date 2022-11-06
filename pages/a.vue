<template>
  <div>
    <Loading v-show="load" />
    <canvas id="main-car"></canvas>
    <Gui />
    <Buttonfloat @openMenu="openMenuFn" @closeMenu="closeMenuFn" />
    <Setting :openModal="this.openModal" @changeColor="colorFn" @openPriceCar="openPriceCarFn" />
    <PriceCar
      @hideCarPart="hideCarPartFn"
      @closePriceCar="closePriceCarFn"
      :openPriceCar="this.openPriceCar"
    />
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
  MixOperation
} from "three";
import { GLTFLoader } from "three/examples/jsm/loaders/GLTFLoader";
import { DRACOLoader } from "three/examples/jsm/loaders/DRACOLoader";
import { DecalGeometry } from 'three/examples/jsm/geometries/DecalGeometry.js';
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls";
import Stats from "three/examples/jsm/libs/stats.module.js";
import NamePart from "~/assets/js/namePart";

export default {
  data() {
    return {
      load: true,
      model: null,
      cubeMap: null,
      openModal: 1,
      openPriceCar: 0,
      tieMaterial: null,
      windowglassMaterial: null,
      rimMaterial: null,
      redglassMaterial: null,
      orangeglassMaterial: null,
      mirrorMaterial: null,
      mattemetalMaterial: null,
      LicPlateBlueMaterial: null,
      LicPlateBlackMaterial: null,
      LicPlateWhiteMaterial: null,
      interiorMaterial: null,
      clearglassMaterial: null,
      chromeMaterial: null,
      carpaintMaterial: null,
      brakediskMaterial: null,
      blackMaterial: null
    };
  },
  methods: {
    colorFn(getNamePart, getColor) {
      var parent = this.model;
      const new_mtl = new MeshPhongMaterial({
        color: parseInt("0x" + getColor.replace("#", "")),
        shininess: 0,
        envMap: this.cubeMap,
        combine: MixOperation,
        reflectivity: 0.1,
        specular: parseInt("0x" + getColor.replace("#", ""))
      });
      if (getNamePart) {
        parent.traverse(o => {
          if (o.isMesh && o.name != null) {
            if (eval(NamePart[getNamePart])) {
              o.material = new_mtl;
            }
          }
        });
      }
    },
    hideCarPartFn(getNamePart) {
      this.resetCar();
      var parent = this.model;
      const new_mtl = new MeshPhongMaterial({
        color: 0xffffff,
        opacity: 0.4,
        transparent: true
      });
      if (getNamePart) {
        parent.traverse(o => {
          if (o.name != null) {
            if (eval(NamePart[getNamePart])) {
              o.material = new_mtl;
            }
          }
        });
      }
    },
    resetCar() {
      var parent = this.model;
      parent.traverse(o => {
        if (o.isMesh && o.name != null) {
          if (eval(NamePart.tie)) {
            o.material = this.tieMaterial;
          }
          if (eval(NamePart.windowglass)) {
            o.material = this.windowglassMaterial;
          }
          if (eval(NamePart.rim)) {
            o.material = this.rimMaterial;
          }
          if (eval(NamePart.redglass)) {
            o.material = this.redglassMaterial;
          }
          if (eval(NamePart.orangeglass)) {
            o.material = this.orangeglassMaterial;
          }
          if (eval(NamePart.mirror)) {
            o.material = this.mirrorMaterial;
          }
          if (eval(NamePart.mattemetal)) {
            o.material = this.mattemetalMaterial;
          }
          if (eval(NamePart.LicPlateBlue)) {
            o.material = this.LicPlateBlueMaterial;
          }
          if (eval(NamePart.LicPlateBlack)) {
            o.material = this.LicPlateBlackMaterial;
          }
          if (eval(NamePart.LicPlateWhite)) {
            o.material = this.LicPlateWhiteMaterial;
          }
          if (eval(NamePart.interior)) {
            o.material = this.interiorMaterial;
          }
          if (eval(NamePart.clearglass)) {
            o.material = this.clearglassMaterial;
          }
          if (eval(NamePart.chrome)) {
            o.material = this.chromeMaterial;
          }
          if (eval(NamePart.carpaint)) {
            o.material = this.carpaintMaterial;
          }
          if (eval(NamePart.brakedisk)) {
            o.material = this.brakediskMaterial;
          }
          if (eval(NamePart.black)) {
            o.material = this.blackMaterial;
          }
        }
      });
    },

    openMenuFn() {
      this.openModal = 1;
    },
    closeMenuFn() {
      this.openModal = 0;
    },
    openPriceCarFn() {
      this.openPriceCar = 1;
    },
    closePriceCarFn() {
      this.resetCar();
      this.openPriceCar = 0;
    }
  },
  mounted() {
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

    // add cubemap

    // "px.png", "nx.png", "py.png", "ny.png", "pz.png", "nz.png";
    // const cubeMap = new CubeTextureLoader()
    //   .setPath("textures/cubemap/")
    //   .load([
    //     "HDR_03_r.jpg",
    //     "HDR_03_l.jpg",
    //     "HDR_03_t.jpg",
    //     "HDR_03_d.jpg",
    //     "HDR_03_f.jpg",
    //     "HDR_03_b.jpg"
    //   ]);
    // that.cubeMap = cubeMap;
    // scene.background = cubeMap;

    // // add floor
    // const floorGeometry = new PlaneGeometry(1000, 1000);
    // var girdTexture = new TextureLoader().load("textures/floor.jpg");
    // girdTexture.repeat.set(1000, 1000);
    // girdTexture.offset.set(0, 0);
    // girdTexture.wrapS = RepeatWrapping;
    // girdTexture.wrapT = RepeatWrapping;

    // const floorMtl = new MeshPhongMaterial({
    //   map: girdTexture,
    //   transparent: true,
    //   opacity: 0.7
    // });
    // var floor = new Mesh(floorGeometry, floorMtl);
    // floor.rotation.x = -0.5 * Math.PI;
    // floor.receiveShadow = true;
    // floor.position.y = -1;
    // scene.add(floor);

    // load model
    var loader = new GLTFLoader();

    const dracoLoader = new DRACOLoader();
    dracoLoader.setDecoderPath( './draco/' );
    loader.setDRACOLoader( dracoLoader );

    loader.load(
      MODEL_PATH,
      function(gltf) {
        theModel = gltf.scene;
        that.model = theModel;

        theModel.traverse(o => {
          if (o.isMesh) {
            if (o.name == "front_treads03") {
              that.tieMaterial = o.material;
            }
            if (o.name == "side_window") {
              that.windowglassMaterial = o.material;
            }
            if (o.name == "front_rim04") {
              that.rimMaterial = o.material;
            }
            if (o.name == "rear_light_red_glass") {
              that.redglassMaterial = o.material;
            }
            if (o.name == "rear_light_lamp_orange") {
              that.orangeglassMaterial = o.material;
            }
            if (o.name == "side_dackward_mirror_glass") {
              that.mirrorMaterial = o.material;
            }
            if (o.name == "front_light_white_lamp") {
              that.mattemetalMaterial = o.material;
            }
            if (o.name == "LicPlate01002_2") {
              that.LicPlateBlueMaterial = o.material;
            }
            if (o.name == "LicPlate01002_1") {
              that.LicPlateBlackMaterial = o.material;
            }
            if (o.name == "LicPlate01002") {
              that.LicPlateWhiteMaterial = o.material;
            }
            if (o.name == "interior01") {
              that.interiorMaterial = o.material;
            }
            if (o.name == "rear_light_reflector_cover") {
              that.clearglassMaterial = o.material;
            }
            if (o.name == "rear_logo") {
              that.chromeMaterial = o.material;
            }
            if (o.name == "body_parts") {
              that.carpaintMaterial = o.material;
            }
            if (o.name == "disk_brake_front04") {
              that.brakediskMaterial = o.material;
            }
            if (o.name == "disk_brake_caliper_front04") {
              that.blackMaterial = o.material;
            }

            o.castShadow = true;
            o.receiveShadow = true;
          }
        });

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

    // const pointLight = new PointLight(0xffffff, 0.6);
    // pointLight.position.set(0, 3, 0);
    // pointLight.distance = 100;
    // scene.add(pointLight);

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
  }
};
</script>
