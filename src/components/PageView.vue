<template>
  <div>
    <template v-if="!isTab">
      <div id="vue-app-effect__sub-router-view">
        <Navigation v-if="title" :title="title" :backShow="!isTab"></Navigation>
        <div class="bd-view" :class="{ 'bd-view-full': !title }">
          <slot></slot>
        </div>
      </div>
    </template>
    <template v-else>
      <Navigation v-if="title" :title="title" :backShow="!isTab"></Navigation>
      <div class="bd-view" :class="{ 'bd-view-full': !title }">
        <slot></slot>
      </div>
    </template>
  </div>
</template>
<script>
import Navigation from "./Navigation";
export default {
  name: "Tab-Page-View",
  components: {
    Navigation,
  },
  props: {
    isTab: {
      type: Boolean,
      default: false,
      discription: "是否是tab页面"
    },
    title: {
      type: String,
      default: "",
      discription: "导航标题, 传值显示导航"
    },
    pullRefresh: {
      type: Function,
      default: null,
      discription: "下拉刷新函数"
    },
    reachBottom: {
      type: Function,
      default: null,
      discription: "上拉加载函数"
    },
    onScroll: {
      type: Function,
      default: null,
      discription: "监听滚动函数"
    }
  }
};
</script>
