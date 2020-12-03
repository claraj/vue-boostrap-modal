<template>
  <div>
   
    <h2>You can edit your favorites in a modal</h2>

    <p>Your favorite color is {{ favorites.color }}</p>
    <p>Your lucky number is {{ favorites.luckyNumber }}</p>

    <!-- b-button is a Bootstrap-Vue shortcut for creating a bootstrap styled button -->
    <!-- an important attribute is the v-b-modal.edit-favorites-modal -->
    <!-- This links the button and makes the modal appear when the button is clicked. --> 
    <!-- Notice the id for the b-modal is the same, edit-favorites-modal  -->
    <b-button v-b-modal.edit-favorites-modal>Edit Favorites</b-button>
    <!-- b-button is a Bootstrap-Vue shortcut for creating a bootstrap styled button -->
    <!-- this is the regular boostrap equivalent to b-button --> 
    <!-- <button class="btn btn-secondary" v-b-modal.edit-favorites-modal>Edit Favorites</button> -->
   
    <!-- The Boostrap modal. This HTML is hidden, Bootstrap will make it visible -->
    <!-- Bootstrap-Vue will take care of styling, and add an OK and a Cancel button -->
    <!-- give the modal an id -->
    <!-- a b-modal component emits a show event when the modal is shown -->
    <!-- a b-modal component emits a ok event when the ok button is clicked -->
    <!-- there are other events, for example, from cancel, or dismissing the modal - see documentation if you need to use those -->
    <b-modal id="edit-favorites-modal" title="Edit Favorites" v-on:show="populate" v-on:ok="save">
      <div class="form-group">
        <label class="form-label" for="favorite-color-input">Favorite color</label>
        <input class="form-control" id="favorite-color-input" v-model="updateColor">
        <label class="form-label" for="lucky-number-input">Lucky number</label>
        <input class="form-control" id="lucky-number-input" v-model="updateLuckyNumber">
      </div>
   </b-modal>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    userFavorites: Object
  },
  data() {
    return {
      favorites: this.userFavorites,   // make a copy to avoid modifying props
      updateColor: '',
      updateLuckyNumber: ''
    }
  },
  methods: {
    populate() {
      this.updateColor = this.favorites.color
      this.updateLuckyNumber = this.favorites.luckyNumber
    },
    save() {
      this.favorites.color = this.updateColor
      this.favorites.luckyNumber = this.updateLuckyNumber
      // todo if you need to notify another component that the data has changed, here's a good place to do it 
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
