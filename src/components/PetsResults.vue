<script>
import PetCard from './PetCard.vue'
export default {
  components: { PetCard },
  props: {
    pets: {
      type: Array,
      required: true
    }
  }
}
</script>

<template>
  <div className="grid grid-cols-1 gap-4 sm:grid-cols-2 lg:grid-cols-3">
    <h1 v-if="pets.length == 0">No Pets Found:(</h1>
    <PetCard
      v-for="pet in this.pets"
      :name="pet.name"
      :id="pet.id"
      :animal="pet.animal"
      :breed="pet.breed"
      :images="pet.images"
      :location="`${pet.city},${pet.state}`"
      :key="pet.id"
    />
  </div>
</template>
