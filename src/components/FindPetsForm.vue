<script>
export default {
  props: ['filterPets', 'sortPets'],
  methods: {
    clearFilter() {
      this.location = ''
      this.animal = ''
      this.filterPets('', '')
    }
  },
  data() {
    return {
      location: '',
      animal: '',
      ANIMALS: ['bird', 'cat', 'dog', 'rabbit', 'reptile']
    }
  }
}
</script>
<template>
  <form className="mb-10 rounded-lg bg-gray-200 p-10 shadow-lg">
    <label htmlFor="location">
      City
      <input
        type="text"
        name="location"
        id="location"
        className="search-input"
        placeholder="City..."
        v-model="location"
      />
    </label>
    <label htmlFor="animal">
      Animal
      <select id="animal" name="animal" className="search-input" v-model="animal">
        <option></option>
        <option v-for="animal in ANIMALS" :key="`animal-${animal}`">{{ animal }}</option>
      </select>
    </label>
    <button
      type="button"
      @click="filterPets(location, animal)"
      className="rounded border-none bg-red-300 px-6 py-2 text-white hover:opacity-50"
    >
      Filter
    </button>
    <button
      type="button"
      @click="sortPets()"
      className="ml-4 rounded border-none bg-red-300 px-6 py-2 text-white hover:opacity-80"
    >
      Sort
    </button>
    <button
      type="button"
      @click="clearFilter()"
      className="ml-4 rounded border-none bg-red-300 px-6 py-2 text-white hover:opacity-80"
    >
      Clear Filter
    </button>
  </form>
</template>
