<script setup lang="ts">
import { shallowRef } from 'vue';
import { TresCanvas, useRenderLoop } from '@tresjs/core';
import { OrbitControls, Plane, Box, Line2 } from '@tresjs/cientos';
import { BasicShadowMap, SRGBColorSpace, NoToneMapping } from 'three';

const gl = {
  clearColor: 'midnightblue',
  shadows: true,
  alpha: false,
  shadowMapType: BasicShadowMap,
  outputColorSpace: SRGBColorSpace,
  toneMapping: NoToneMapping,
}

const boxRef = shallowRef(null) as { value: { rotation: { y: number, z: number } } | null };

// const { onLoop } = useRenderLoop();

// onLoop(({ delta, elapsed }) => {
//   if (boxRef.value) {
//     boxRef.value.rotation.y += delta;
//     boxRef.value.rotation.z = elapsed * 0.2;
//   }
// });
</script>

<template>
  <TresCanvas v-bind="gl" shadows alpha window-size>
    <OrbitControls />
    <TresPerspectiveCamera :position="[1, 2, 5]" :fov="45" :aspect="1" :near="0.1" :far="1000" />
    <TresMesh ref="boxRef" :scale="1" cast-shadow>
      <!-- <TresBoxGeometry :args="[1, 1, 1]" /> -->
      <Plane :args="[1, 1, 1]" :position="[0, 0, 0]">
        <TresMeshBasicMaterial :color="'#DC143C'" :transparent="true" :opacity="0.25" />
      </Plane>
      <Plane :args="[1, 1, 1]" :position="[0, 1, 0]">
        <TresMeshBasicMaterial :color="'#DC143C'" :transparent="true" :opacity="0.25" />
      </Plane>
      <Plane :args="[1, 1, 1]" :position="[0, 0.5, 0]">
        <TresMeshBasicMaterial :color="'yellow'" :transparent="true" :opacity="0.25" />
      </Plane>
      <Line2 :points="[[0.5, 0, 0.5], [0.5, 0, -0.5], [0.5, 0, 0], [0.5, 0, 0]]" :line-width="0.001" color="#DC143C" />
    </TresMesh>
  </TresCanvas>
</template>

<style>
.cane {
  border: 1px solid green
}
</style>