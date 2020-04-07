<svelte:head>
  <title>Aframe Example</title>
</svelte:head>

<a-scene>
  <a-assets>
    <img
      id="boxTexture"
      src="https://ericdavidsmith.com/ericdavidsmith.png"
      alt="Eric David Smith" />
    <img
      id="skyTexture"
      src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2553&q=80"
      alt="The Beach" />
  </a-assets>

  <a-box src="#boxTexture" position="0 2 -5" rotation="0 45 45" scale="2 2 2" />

  <a-sky src="#skyTexture" />
</a-scene>
