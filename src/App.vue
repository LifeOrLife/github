<script setup lang="ts">
import { ref } from 'vue'
import repositoryCard from '@/components/repositoryCard.vue'

type Repositoty = Record<string, any>

const word = ref('')
const repositories = ref<Repositoty[]>([])
const getStared = async () => {
  const result = await fetch(`https://api.github.com/users/${word.value}/starred`).then(async (res) => {
    return await res.json()
  })
  repositories.value = result
  console.log(result)
}
</script>

<template>
  <header>
    <div class="title">
      Search the info of the github
    </div>
  </header>
  <main>
    <div class="user-name">
      <input class="word" v-model="word" @keydown.enter="getStared" />
    </div>
    <div class="card-list">
      <repositoryCard 
        v-for="card in repositories"
        :avatar="card.owner.avatar_url"
        :author="card.owner.login"
        :name="card.name"
        :authorLink="card.owner.html_url"
        :reposLink="card.html_url"
        :link="card.html_url"
      />
    </div>
  </main>
</template>

<style lang="scss" scoped>
header {
  line-height: 1.5;
}
.title {
  text-align: center;
}
.user-name {
  width: 800px;
  max-width: 80%;
  margin: 30px auto 0;
}
.word {
  width: 100%;
  height: 35px;
  padding: 0 10px;
  border-radius: 3px;
  border: 1px solid #ccc;
  outline: none;
  text-align: center;
  &:focus {
    border-color: aqua;
    box-shadow: 0 0 5px 5px rgba(0, 255, 255, .2);
  }
}
.card-list {
  display: flex;
  flex-wrap: wrap;
}
</style>
