<template>
  <HelloWorld />
  <Form />
  <CardList />
  
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Form from './components/Form.vue'
import CardList from './components/CardList.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    Form,
    CardList
  }
}
</script>


