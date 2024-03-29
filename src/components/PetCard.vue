<script>
export default {
  props: ['name', 'id', 'animal', 'breed', 'images', 'location']
}
</script>
<template>
  <div class="relative block">
    <div className="image-container">
      <img :src="this.images[0]" :alt="this.name" />
    </div>
    <div>
      <h1>{{ this.name }}</h1>
      <h2>{{ `${animal} — ${breed} — ${location}` }}</h2>
    </div>
  </div>
</template>
