<template>
  <div class="card">
      {{italianTitle}}
      {{originalTitle}}
      {{language}}
      {{rating}}
  </div>
</template>

<script>
export default {
    name: "Card",
    props: ['italianTitle','originalTitle','language','rating']
}
</script>

<style>

</style>