<template>
  <!-- add html here -->
  <ol>
    <li v-for="note in notes">
      <pre>
        {{note | json}}
      </pre>
    </li>
  </ol>
</template>
<script>
// add js here
import Firebase from 'firebase'
export default {
  data () {
    return {
      notes: []
    }
  },
  ready () {
    let firebase = new Firebase('https://crackling-inferno-7625.firebaseio.com/')
    firebase.child('notes').on('child_added', (snapshot) => {
      let note = snapshot.val()
      this.notes.unshift(note)
    })
  }
}
</script>
<style>
/* add css here */
</style>
