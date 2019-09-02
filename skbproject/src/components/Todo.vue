<template>
  <div class="Todo">
    <div class="center">
      <div>
        <h3>Jquery To Do List</h3>
        <span>
          <p>Simple Todo List with adding and filter by diff status.</p>
        </span>
      </div>
      <div>
        <input type="text"/>
        <div id="button">Add</div>
      </div>
      <div class="list-main">
      </div>
      <div class="choose-list">
        <div>All</div>
        <div>Active</div>
        <div>complete</div>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: "Todo",
  data() {
    return {
    };
  },
  components: {
  },
  methods: {
  } ,
  computed : {
  }
};
</script>

<style scoped>
#button {
  display: inline-block;
  background-color: antiquewhite;
  color: #ffffff;
  padding: 5px 15px;
}
.choose-list div {
  display: inline-block;
  margin: 5px 10px;
}
</style>
