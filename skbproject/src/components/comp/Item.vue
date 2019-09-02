<template>
  <nav class="Item" :class="{ choosed: isChoosed }">
    <input type="checkbox" v-model="isChoosed" />
    {{message}}
  </nav>
</template>

<script type="text/ecmascript-6">
export default {
  name: "Item",
  data() {
    return {
      isChoosed: false
    };
  },
  components: {},
  props: ["message","id"],
  watch : {
    'isChoosed' : function(newVal,oldVal) {
      this.$emit("chooseStatusChange",newVal,this.id);
    }
  }
};
</script>

<style scoped>
.Item {
  color: #999;
}
.choosed {
  text-decoration: line-through;
}
</style>
