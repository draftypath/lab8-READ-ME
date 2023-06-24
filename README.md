var createScene = function () {
    // This creates a basic Babylon Scene object (non-mesh)
    var scene = new BABYLON.Scene(engine);

    var camera = new BABYLON.ArcRotateCamera("camera", BABYLON.Tools.ToRadians(90), BABYLON.Tools.ToRadians(65), 10, BABYLON.Vector3.Zero(), scene);

    // This attaches the camera to the canvas
    camera.attachControl(canvas, true);

    // This creates a light, aiming 0,1,0 - to the sky (non-mesh)
    var light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 1), scene);

    // Default intensity is 1. Let's dim the light a small amount
    light.intensity = 0.5;

    // Our built-in 'ground' shape.
    var ground = BABYLON.MeshBuilder.CreateGround("ground", { width: 30, height: 30 }, scene);

    // Create a material for the ground
    var groundMaterial = new BABYLON.StandardMaterial("Ground Material", scene);

    // Set the diffuse color of the material to red
    groundMaterial.diffuseColor = new BABYLON.Color3(1, 0, 0); // Red

    // Assign the material to the ground mesh
    ground.material = groundMaterial;

    BABYLON.SceneLoader.ImportMesh("", Assets.meshes.Yeti.rootUrl, Assets.meshes.Yeti.filename, scene, function (newMeshes) {
        newMeshes[0].scaling = new BABYLON.Vector3(0.1, 0.1, 0.1);
    });

    return scene;
};
