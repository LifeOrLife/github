<script setup lang="ts">

defineProps<{
  avatar: string
  author: string
  authorLink: string
  reposLink: string
  name: string
  link: string
}>()
</script>
<template>
  <div class="repository-card">
    <div class="avatar">
      <img :src="avatar" alt="" />
      <a class="name" :href="authorLink" target="_blank">@ {{ author }}</a>
    </div>
    <div class="link">
      <a :href="reposLink" target="_blank">{{ reposLink }}</a>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.repository-card {
  padding: 10px;
  border-radius: 5px;
  width: 550px;
  height: 270px;
  margin: 10px;
  background: radial-gradient(147.16% 118.37% at 50% 120.63%,#203d57 14.24%,#1a283b 29.36%,#14101f 47.94%,#0e0c14 68.23%,#0c0b11 89.06%,#0d0b13 100%);
  img {
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }
  .name {
    color: #fff;
    margin-left: 10px;
  }
  .avatar {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }
  a {
    color: #fff;
  }
}
</style>