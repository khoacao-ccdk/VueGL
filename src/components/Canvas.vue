<template>
    <div id="app">
        <vgl-renderer id="canvas" style="height: 60vh">
            <template #scene>
                <vgl-scene>
                    <vgl-mesh antialias 
                        :position-x="x"
                        :position-y="y"
                        :position-z="z"
                    >
                        <template #geometry>
                            <vgl-sphere-geometry />
                        </template>
                        <vgl-axes-helper :size=140></vgl-axes-helper>
                        <template #material>
                            <vgl-mesh-standard-material />
                        </template>
                    </vgl-mesh>
                    <vgl-directional-light 
                        :position-x="1" 
                        :position-y="1.5"   
                        :position-z="1" 
                    />
                </vgl-scene>
                </template>
            <template #camera>
                <vgl-perspective-camera 
                    position="rectangular"
                    :position-x="camX"
                    :position-y="camY"
                    :position-z="camZ" 
                    rotation="lookAt"
                />
            </template>
        </vgl-renderer>
        <aside class="control-panel">
            <h3>Object Position</h3>
            <label> x 
                <input 
                    v-model.number="x"
                    min = "-1"
                    max = "1"
                    step = "0.01"
                    type = "range"
                >
            </label>
            <label> y 
                <input 
                    v-model.number="y"
                    min = "-1"
                    max = "1"
                    step = "0.01"
                    type = "range"
                >
            </label>
            <label> z
                <input 
                    v-model.number="z"
                    min = "-1"
                    max = "1"
                    step = "0.01"
                    type = "range"
                >
            </label>
            <h3>Camera Position</h3>
            <label> Camera's x 
                <input 
                    v-model.number="camX"
                    min = "-10"
                    max = "10"
                    step = "0.1"
                    type = "range"
                >
            </label>
            <label> Camera's y 
                <input 
                    v-model.number="camY"
                    min = "-10"
                    max = "10"
                    step = "0.1"
                    type = "range"
                >
            </label>
            <label> Camera's z
                <input 
                    v-model.number="camZ"
                    min = "-10"
                    max = "10"
                    step = "0.1"
                    type = "range"
                >
            </label>
        </aside>
    </div>
</template>

<script>
import Vue from 'vue';
import * as VueGL from 'vue-gl';

Object.entries(VueGL).forEach(([name, component]) => Vue.component(name, component));


export default {
  name: "Canvas",
  data: ()=>({
      x: 0,
      y: 0,
      z: 0,
      upward: true,
      camX: 0,
      camY: 0,
      camZ: 0,
  }),

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
