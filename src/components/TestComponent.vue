<template>
  <div>
    test
  </div>
</template>
<script>
export default {
  props: {
    id: {
      required: true,
      type: String
    }
  },
  created: function() {
    console.log('id is : ' + this.id)
    console.log(this.props)
  }
}
</script>

