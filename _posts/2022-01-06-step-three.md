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

To recreate a skybox, we can simply choose a color for our scene background. In this case we will use black. Add this snippet after the code for the **light**.

```javascript
    /**** Sky Color *****/
    scene.clearColor = BABYLON.Color3.Black();
```

### Ground Material & Texture

The code below creates a material and texture for the ground. Add this snippet after the code for the **ground**.

```javascript
    //This provides our ground with a given texture, by first declaring the material object
    var groundMat = new BABYLON.StandardMaterial("groundMaterial");
    //We define where the texture for the material is coming from
    groundMat.diffuseTexture = new BABYLON.Texture("https://raw.githubusercontent.com/gcordido/babylon-student-workshop/gh-pages/textures/grass.jpg", scene);
    //And determine how we want to spread said texture across the ground.
    groundMat.diffuseTexture.uScale = 6;
    groundMat.diffuseTexture.vScale = 6;
    //Finally, we assign the groundMat object as the our ground object's material.
    ground.material = groundMat;
```

## Complete Code

Provided below is the complete code for this step of the workshop.

```javascript
var createScene = function () {
    //Creating a Babylon Scene Object, using the babylon engine.
    var scene = new BABYLON.Scene(engine);

    //Create a camera object, which allows us to see the world we're building.
    var camera = new BABYLON.ArcRotateCamera("camera", -Math.PI / 2, Math.PI / 2.5, 10, new BABYLON.Vector3(0, 0, 0));
   
   //Define where the camera will be attached, in this case the canvas we are working in.
    camera.attachControl(canvas, true);

    //Creates a hemispheric light for the scene (allows for visibility of our objects)
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);

    /**** Sky Color *****/
    scene.clearColor = BABYLON.Color3.Black();

    //Creates a ground object, which allows us to have a more world-like scene, as well as guidance as to where to drop future objects.
    var ground = BABYLON.MeshBuilder.CreateGround("ground", { width: 40, height: 40}, scene);

    //This provides our ground with a given texture, by first declaring the material object
    var groundMat = new BABYLON.StandardMaterial("groundMaterial");
    //We define where the texture for the material is coming from
    groundMat.diffuseTexture = new BABYLON.Texture("https://raw.githubusercontent.com/gcordido/babylon-student-workshop/gh-pages/textures/grass.jpg", scene);
    //And determine how we want to spread said texture across the ground.
    groundMat.diffuseTexture.uScale = 6;
    groundMat.diffuseTexture.vScale = 6;
    //Finally, we assign the groundMat object as the our ground object's material.
    ground.material = groundMat;

    return scene;
};
```

<ul class="actions">
<li><a href="https://gcordido.github.io/babylon-student-workshop/jekyll/update/2022/01/07/step-two.html" class="button special">Back</a></li>
<li><a href="https://gcordido.github.io/babylon-student-workshop/jekyll/update/2022/01/05/step-four.html" class="button">Next</a></li>
</ul>