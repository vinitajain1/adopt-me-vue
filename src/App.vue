<script>
import AdoptMeHeader from './components/AdoptMeHeader.vue'
import FindPetsForm from './components/FindPetsForm.vue'
import data from './assets/data.js'
import PetsResults from './components/PetsResults.vue'
export default {
  components: {
    AdoptMeHeader,
    FindPetsForm,
    PetsResults
  },
  data() {
    return { petsData: Object.create(data), filteredList: Object.create(data) }
  },
  methods: {
    filterPets(location, animal) {
      if (location.trim() == '' || animal == '') {
        this.filteredList.pets = Object.create(data.pets)
      } else {
        const newPets = this.petsData.pets.filter((pet) => {
          return (
            pet.city.toLowerCase() == location.toLowerCase() &&
            pet.animal.toLowerCase() == animal.toLowerCase()
          )
        })
        this.filteredList.pets = newPets
      }
    },
    sortPets() {
      this.filteredList.pets.sort((pet1, pet2) => {
        if (pet1.name < pet2.name) {
          return -1
        }
        if (pet1.name > pet2.name) {
          return 1
        }
        return 0
      })
    }
  }
}
</script>
<template>
  <AdoptMeHeader />
  <div className="my-0 mx-auto grid w-11/12 grid-cols-2 gap-4">
    <FindPetsForm :filterPets="filterPets" :sortPets="sortPets" />
    <PetsResults :pets="filteredList.pets" />
  </div>
</template>
