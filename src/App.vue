<template>
  <FieldView :data="trajectory"/>
</template>

<script setup>
import FieldView from "@/components/FieldView.vue";
import trajectory from "../resources/trajectory.json";

</script>

<style>
body, html {
    height: 100%;
}
* {
    padding: 0;
    margin: 0;
}
</style>
