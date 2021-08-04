<template>
  <div class="home">
    <void-component
      text="Хэдер"
      color="#ff4a4a"
    />
    <void-component
      text="Преимущества даркстора"
      color="#88ef98"
    />
    <content-container />
    <void-component
      text="Футер"
      color="#1c9ef2"
    />
  </div>
</template>

<script>
  import voidComponent from "../components/VoidComponent.vue";
  import contentContainer from "../components/ContentContainer.vue";

  export default {
    name: 'Home',
    components: {
      voidComponent,
      contentContainer
    }
  }
</script>
