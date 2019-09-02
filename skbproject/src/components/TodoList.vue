<template>
  <nav class="TodoList">
    <section class="main">
      <article>
        <h2>Jquery To Do List</h2>
        <p>
          <em>Simple Todo List with adding and filter by diff status.</em>
        </p>
      </article>
      <article>
        <input class="input-text" type="text" name="ListItem" v-model="currMsg" />
        <div id="button" @click="addMsg()">Add</div>
      </article>
      <article class="list">
        <Item v-show="isShowByType(index)" @chooseStatusChange="chooseStatusChange" :message="item.msg" :id="index" v-for="(item,index) in msgList" :key="index"></Item>
      </article>
      <article class="bottom">
        <div :class="{selected: type == 0}" @click="changeType(0)">All</div>
        <div :class="{selected: type == 1}" @click="changeType(1)">Active</div>
        <div :class="{selected: type == 2}" @click="changeType(2)">complete</div>
      </article>
    </section>
  </nav>
</template>

<script type="text/ecmascript-6">
import Item from "./comp/Item";
export default {
  name: "TodoList",
  data() {
    return {
      msgList: [],
      currMsg: "",
      type : 0 //0为all，1为active，2为complete
    };
  },
  components: {
    Item
  },
  methods: {
    addMsg: function() {
      this.msgList.push({msg:this.currMsg,choosed:false});
    },
    chooseStatusChange : function(newVal,id) {
      this.msgList[id].choosed = newVal;
    },
    changeType : function(num) {
      console.log(num);
      this.type = num;
    },
    isShowByType: function(index) {
      let isShow = true;
      switch(this.type) {
        case 0 : isShow = true; break;
        case 1 : this.msgList[index].choosed?isShow = false:isShow = true; break;
        case 2 : this.msgList[index].choosed?isShow = true:isShow = false; break;
      }
      return isShow;
    }
  } ,
  computed : {
  }
};
</script>

<style scoped>
.TodoList {
  display: flex;
  justify-content: center;
}
.main {
  padding: 20px;
  width: 400px;
  background: white;
  border-radius: 5px;
}

.input-text {
  width: 70%;
}
input {
  padding: 4px 15px 4px 0;
}
#button {
  display: inline-block;
  background-color: #fc999b;
  color: #ffffff;
  border-radius: 5px;
  text-align: center;
  margin-top: 2px;
  padding: 5px 15px;
}
#button:hover {
  opacity: 0.7;
  cursor: pointer;
}
.list {
  margin: 20px;
  text-align: left;
}
.bottom {
  display: flex;
  flex-wrap: nowrap;
}
.bottom div {
  padding: 10px;
  margin: 5px 10px;
  color: #fc999b;
}
.bottom div:hover  {
  border: 1px solid;
  border-radius: 3px;
  cursor: pointer;
}
.selected {
  border: 1px solid;
  border-radius: 3px;
  cursor: pointer;
}
</style>
