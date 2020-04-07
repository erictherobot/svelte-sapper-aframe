<svelte:head>
  <title>Aframe Example</title>
</svelte:head>

<a-scene environment="preset: forest">
  <a-assets>
    <img
      id="boxTexture"
      src="https://ericdavidsmith.com/ericdavidsmith.png"
      alt="Eric David Smith" />
    <img
      id="skyTexture"
      src="https://images.unsplash.com/photo-1460411794035-42aac080490a?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1950&q=80"
      alt="The Beach" />
  </a-assets>
  <a-box
    src="#boxTexture"
    position="0 2 -5"
    rotation="0 45 45"
    scale="2 2 2"
    animation__position="property: object3D.position.y; to: 2.2; dir: alternate;
    dur: 2000; loop: true"
    animation__mouseenter="property: scale; to: 2.3 2.3 2.3; dur: 300;
    startEvents: mouseenter"
    animation__mouseleave="property: scale; to: 2 2 2; dur: 300; startEvents:
    mouseleave" />

  <a-entity
    text="value: I can float like a cloud; color: red; width: 4; anchor: align"
    position="-1 0.2 -3 0"
    scale="1.5 1.5 1.5" />
  <a-camera>
    <a-cursor color="red" />
  </a-camera>
  <a-sky src="#skyTexture" />
</a-scene>
