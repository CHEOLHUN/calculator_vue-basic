<template>
  <transition-group name="list" tag="div">
    <div v-for="(item, index) in propsHistory" :key="index" class="CalcHistoy__Item">
      <span>{{item}}</span>
      <button class="CalcHistoy__DeleteBtn" @click="onClickDelete(index, item)">삭제</button>
    </div>
  </transition-group>
</template>

<script>
export default {
  props: ["propsHistory"],
  methods: {
    onClickDelete: function (index, item) {
      this.$emit("emitDelete", {
        index: index,
        item: item,
      });
    },
  },
};
</script>

<style scoped>
.CalcHistoy__Item {
  position: relative;
  width: 100%;
  height: 30;
  background-color: #7f8082;
  margin-top: 10px;
  padding: 5px;
  color: #ffffff;
  font-weight: 700;
  box-sizing: border-box;
  letter-spacing: 10px;
  text-align: center;
}

.CalcHistoy__DeleteBtn {
  position: absolute;
  right: 5px;
  top: 3px;
}


/* List Transitions */
.list-enter-active,
.list-leave-active {
  transition: all 1s;
}
.list-enter,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>