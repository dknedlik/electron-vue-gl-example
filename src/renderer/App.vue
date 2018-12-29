<template>
<div id="app">
    <aside class="control-panel">
    <h3>Position</h3>
    <label>x<input type="range" v-model="x"></label>
    <label>y<input type="range" v-model="y"></label>
    <label>z<input type="range" v-model="z"></label>
  </aside>
  <vgl-namespace style="display: flex;">
      <vgl-scene name="sphere">
        <vgl-sphere-geometry name="sphere" radius=25></vgl-sphere-geometry>
        <vgl-mesh-standard-material name="std"></vgl-mesh-standard-material>
        <vgl-mesh geometry="sphere" material="std" :position="`${x} ${y} ${z}`"></vgl-mesh>
        <vgl-axes-helper size=140></vgl-axes-helper>
        <vgl-ambient-light color="#ffeecc"></vgl-ambient-light>
        <vgl-directional-light position="0 1 1"></vgl-directional-light>
      </vgl-scene>
    <vgl-scene name="scn">
      <vgl-box-geometry name="cube" width=3 height=5 depth=10></vgl-box-geometry>
      <vgl-mesh-standard-material name="std"></vgl-mesh-standard-material>
      <vgl-mesh geometry="cube" material="std"></vgl-mesh>
      <vgl-ambient-light color="#ffeecc"></vgl-ambient-light>
      <vgl-directional-light position="0 1 1"></vgl-directional-light>
    </vgl-scene>
    <vgl-renderer scene="sphere" camera="cmr3" antialias style="height: 100vh; flex: 1;">
      <vgl-perspective-camera name="cmr3" orbit-position="200 1 0.5"></vgl-perspective-camera>
    </vgl-renderer>
    <div style="width: 1px;"></div>
    <vgl-renderer scene="scn" camera="cmr1" antialias style="height: 100vh; flex: 2;">
      <vgl-perspective-camera name="cmr1" orbit-position="20 1 0.5"></vgl-perspective-camera>
    </vgl-renderer>
  </vgl-namespace>
</div>
</template>

<script>
  export default {
    name: 'vuegl-app',
    data () {
      return {
        x: 50,
        y: 50,
        z: 50
      }
    }
  }
</script>

<style>
  /* CSS */
</style>
