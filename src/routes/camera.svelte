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
      src="https://images.squarespace-cdn.com/content/v1/5568ec94e4b06c17240d5220/1443508568279-5KM5IBNCU4HDIQGMTCC3/ke17ZwdGBToddI8pDm48kBpzt4_K496Ao-aLooMTCTp7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z4YTzHvnKhyp6Da-NYroOW3ZGjoBKy3azqku80C789l0plef_PmwB6-3GP4qDbCUv9cfxFbOETjyuzxeVcrr-Ci5fj66QIwtSm7rXFpMnU6ig/Homepage+LEI.jpg?format=2500w"
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
