<template>
  <div :class="[$style.position]">
    <v-btn color="#039BE5" elevation="7" fab small dark @click="openMenu">
      <v-icon size="18" v-show="!status">mdi-pencil</v-icon>
      <v-icon size="18" v-show="status">mdi-close</v-icon>
    </v-btn>
  </div>
</template>
<style>
</style>
<style module>
.position {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  z-index: 1;
}
</style>

<script>
export default {
  data() {
    return {
      fab: false,
      status: true
    };
  },
  methods: {
    openMenu() {
      if (this.status) {
        this.status = false;
         this.$emit("closeMenu");
      } else {
        this.status = true;
         this.$emit("openMenu");
      }
     
    }
  }
};
</script>
