<svelte:head>
  <title>Aframe Gallery Example</title>
</svelte:head>

<a-scene>
  <a-box dragndrop position="-2 0.5 -3" rotation="0 45 0" color="#ff0" shadow>
    <a-entity
      template="src: #link"
      data-src="#cubes"
      data-thumb="#cubes-thumb"
      geometry="primitive: plane; width: 2.8; height: auto"
      material="color: blue"
      text="value: Mike's big idea" />
  </a-box>

  <a-box dragndrop position="0 0 -3" rotation="0 45 0" color="#ff0">
    <a-entity
      template="src: #link"
      data-src="#room2"
      data-thumb="#room2-thumb"
      geometry="primitive: plane; width: 2.8; height: auto"
      material="color: blue"
      text="value: Jane's big idea" />
  </a-box>
  <a-assets>
    <img
      id="room2"
      crossorigin="anonymous"
      src="https://cdn.aframe.io/360-image-gallery-boilerplate/img/city.jpg" />
    <img id="room2-thumb" crossorigin="anonymous" src="/sticky.png" />
    <img id="cubes-thumb" crossorigin="anonymous" src="/sticky.png" />
    <img id="sechelt-thumb" crossorigin="anonymous" src="/sticky.png" />
    <audio
      id="click-sound"
      crossorigin="anonymous"
      src="https://cdn.aframe.io/360-image-gallery-boilerplate/audio/click.ogg" />
    <img id="cubes" crossorigin="anonymous" src="/brick.jpg" />
    <img
      id="sechelt"
      crossorigin="anonymous"
      src="https://cdn.aframe.io/360-image-gallery-boilerplate/img/sechelt.jpg" />

    <!-- Image link template to be reused. -->
    <script id="link" type="text/html">
      ;<a-entity
        class="link"
        geometry="primitive: plane; height: 1; width: 1"
        material="shader: flat; src: ${thumb}"
        event-set__mouseenter="scale: 1.2 1.2 1"
        event-set__mouseleave="scale: 1 1 1"
        event-set__click="_target: #image-360; _delay: 300; material.src: ${src}"
        proxy-event="event: click; to: #image-360; as: fade"
        sound="on: click; src: #click-sound"></a-entity>
    </script>
  </a-assets>

  <!-- 360-degree image. -->
  <a-sky
    id="image-360"
    radius="10"
    src="#room2"
    animation__fade="property: components.material.material.color; type: color;
    from: #FFF; to: #000; dur: 300; startEvents: fade"
    animation__fadeback="property: components.material.material.color; type:
    color; from: #000; to: #FFF; dur: 300; startEvents: animationcomplete__fade" />

  <!-- Image links. -->
  <!-- <a-entity id="links" layout="type: line; margin: 1.5" position="0 -1 -4">
    <a-entity
      template="src: #link"
      data-src="#cubes"
      data-thumb="#cubes-thumb" />
    <a-entity
      template="src: #link"
      data-src="#room2"
      data-thumb="#room2-thumb" />
    <a-entity
      template="src: #link"
      data-src="#sechelt"
      data-thumb="#sechelt-thumb" />
  </a-entity> -->

  <!-- Camera + cursor. -->
  <a-entity id="camera" camera look-controls>
    <a-cursor
      id="cursor"
      animation__click="property: scale; startEvents: click; from: 0.1 0.1 0.1;
      to: 1 1 1; dur: 150"
      animation__fusing="property: fusing; startEvents: fusing; from: 1 1 1; to:
      0.1 0.1 0.1; dur: 1500"
      event-set__mouseenter="_event: mouseenter; color: springgreen"
      event-set__mouseleave="_event: mouseleave; color: black"
      raycaster="objects: .link" />
  </a-entity>
</a-scene>
