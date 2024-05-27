<script setup lang="ts">
import { TresCanvas } from '@tresjs/core';
// import { OrbitControls } from '@tresjs/cientos';
</script>

<template>
  <TresCanvas clearColor='midnightblue' window-size>
    <!-- <OrbitControls /> -->
    <TresPerspectiveCamera />
    <TresMesh>
      <TresBoxGeometry :args="[1, 1, 1]" />
      <TresMeshBasicMaterial :color="'#DC143C'" :transparent="true" :opacity="0.25" />
    </TresMesh>
  </TresCanvas>
</template>
