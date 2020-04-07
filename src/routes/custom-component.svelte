<script>
  import { onMount } from 'svelte'

  onMount(() => {
    AFRAME.registerComponent('follow', {
      schema: {
        target: { type: 'selector' },
        speed: { type: 'number' },
      },

      init: function() {
        this.directionVec3 = new THREE.Vector3()
      },

      tick: function(time, timeDelta) {
        var directionVec3 = this.directionVec3

        // Grab position vectors (THREE.Vector3) from the entities' three.js objects.
        var targetPosition = this.data.target.object3D.position
        var currentPosition = this.el.object3D.position

        // Subtract the vectors to get the direction the entity should head in.
        directionVec3.copy(targetPosition).sub(currentPosition)

        // Calculate the distance.
        var distance = directionVec3.length()

        // Don't go any closer if a close proximity has been reached.
        if (distance < 1) {
          return
        }

        // Scale the direction vector's magnitude down to match the speed.
        var factor = this.data.speed / distance
        ;['x', 'y', 'z'].forEach(function(axis) {
          directionVec3[axis] *= factor * (timeDelta / 1000)
        })

        // Translate the entity in the direction towards the target.
        this.el.setAttribute('position', {
          x: currentPosition.x + directionVec3.x,
          y: currentPosition.y + directionVec3.y,
          z: currentPosition.z + directionVec3.z,
        })
      },
    })
  })
</script>

<a-scene>
  <a-box id="target-box" color="#5E82C5" position="-3 0 -5" />
  <a-box
    follow="target: #target-box; speed: 1"
    color="#FF6B6B"
    position="3 0 -5" />
</a-scene>
