---
title: "Squares Game"
categories:
  - Game
tags:
  - Unity
---

Play the squares game, a game I made in Unity and exported to WebGL - a port of a game I originally created on a TI-83+ Silver Edition calculator in TI-BASIC in the early 2000s.

If on a mobile device, try playing in landscape mode.

Use right-click or long hold if on mobile device to toggle pattern mode.

Objective: change all white squares to black in the fewest moves possible.

<link rel="stylesheet" href="/assets/games/squares_game/TemplateData/style.css">
<div id="unity-container" class="unity-desktop">
  <canvas id="unity-canvas"></canvas>
  <div id="unity-loading-bar">
    <div id="unity-logo"></div>
    <div id="unity-progress-bar-empty">
      <div id="unity-progress-bar-full"></div>
    </div>
  </div>
  <div id="unity-footer">
    <div id="unity-webgl-logo"></div>
    <div id="unity-fullscreen-button"></div>
    <div id="unity-build-title">Squares</div>
  </div>
</div>
<script>
  var buildUrl = "/assets/games/squares_game/Build";
  var loaderUrl = buildUrl + "/squares_game.loader.js";
  var config = {
    dataUrl: buildUrl + "/squares_game.data.unityweb",
    frameworkUrl: buildUrl + "/squares_game.framework.js.unityweb",
    codeUrl: buildUrl + "/squares_game.wasm.unityweb",
    streamingAssetsUrl: "StreamingAssets",
    companyName: "DefaultCompany",
    productName: "Squares",
    productVersion: "0.1",
  };

  var container = document.querySelector("#unity-container");
  var canvas = document.querySelector("#unity-canvas");
  var loadingBar = document.querySelector("#unity-loading-bar");
  var progressBarFull = document.querySelector("#unity-progress-bar-full");
  var fullscreenButton = document.querySelector("#unity-fullscreen-button");

  if (/iPhone|iPad|iPod|Android/i.test(navigator.userAgent)) {
    container.className = "unity-mobile";
    config.devicePixelRatio = 1;
  } else {
    canvas.style.width = "960px";
    canvas.style.height = "600px";
  }
  loadingBar.style.display = "block";

  var script = document.createElement("script");
  script.src = loaderUrl;
  script.onload = () => {
    createUnityInstance(canvas, config, (progress) => {
      progressBarFull.style.width = 100 * progress + "%";
    }).then((unityInstance) => {
      loadingBar.style.display = "none";
      fullscreenButton.onclick = () => {
        unityInstance.SetFullscreen(1);
      };
    }).catch((message) => {
      alert(message);
    });
  };
  document.body.appendChild(script);
</script>