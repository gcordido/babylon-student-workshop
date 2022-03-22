---
layout: default
title:  "Step Three"
date:   2022-01-06 12:00:00 -0400
categories: jekyll update
---
## Add Materials and Textures

Materials give your meshes color and texture. One material in Babylon.js can be used to cover as many meshes as you wish. They can be displayed as a wire-frame, scaled and offset across a mesh, have degrees of transparency and be blended. You can apply multiple materials on one mesh and use a dynamic texture as a material that you can draw and write on in real time.

Use the code snippets below to create a material and texture for the sky and ground within the Hall of Fame scene.

## Code Snippets

### Sky

The code below creates a black sky for the scene. Add this snippet after the code for the **light**.

```javascript
    /**** Sky Color *****/
    scene.clearColor = BABYLON.Color3.Black();
```

### Ground Material & Texture

The code below creates a material and texture for the ground. Add this snippet after the code for the **ground**.

```javascript
    var groundMat = new BABYLON.StandardMaterial("groundMaterial");
    groundMat.diffuseTexture = new BABYLON.Texture("https://raw.githubusercontent.com/aprilspeight/workshop-babylonjs/gh-pages/textures/brown-wood.jpg", scene);   
    groundMat.diffuseTexture.uScale = 4;
    groundMat.diffuseTexture.vScale = 4;
    groundMat.specularColor = new BABYLON.Color3(.1, .1, .1);
    ground.material = groundMat;
```

## Complete Code

Provided below is the complete code for this step of the workshop.

```javascript
var createScene = function () {
    /**** This creates a basic Babylon Scene object *****/
    var scene = new BABYLON.Scene(engine);

    /**** This creates a camera *****/
    const camera = new BABYLON.ArcRotateCamera("camera", -Math.PI / 2, Math.PI / 2.5, 10, new BABYLON.Vector3(0, 0, 0));

    /***** This attaches the camera to the canvas *****/
    camera.attachControl(canvas, true);

    /***** This creates a light *****/
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);

    /**** Sky Color *****/
    scene.clearColor = BABYLON.Color3.Black();

    /***** This creates a ground *****/
    var ground = BABYLON.MeshBuilder.CreateGround("ground", { height: 7, width: 7, subdivisions: 4 }, scene);
    var groundMat = new BABYLON.StandardMaterial("groundMaterial");
    groundMat.diffuseTexture = new BABYLON.Texture("https://raw.githubusercontent.com/aprilspeight/workshop-babylonjs/gh-pages/textures/brown-wood.jpg", scene);   
    groundMat.diffuseTexture.uScale = 4;
    groundMat.diffuseTexture.vScale = 4;
    groundMat.specularColor = new BABYLON.Color3(.1, .1, .1);
    ground.material = groundMat;
    
    return scene;
};
```

<ul class="actions">
<li><a href="https://aprilspeight.github.io/workshop-babylonjs/jekyll/update/2022/01/07/step-two.html" class="button special">Back</a></li>
<li><a href="https://aprilspeight.github.io/workshop-babylonjs/jekyll/update/2022/01/05/step-four.html" class="button">Next</a></li>
</ul>