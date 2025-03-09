<script setup lang="ts">
import type { Member } from '~/interfaces';
import OneMember from './OneMember.vue';

const memberList = useState<Map<number, Member>>("memberList")
const totalPoints = computed((): number => {
  let totalPoints = 0
  memberList.value.forEach(member => {
    totalPoints += member.points
  });
  return totalPoints
})
</script>

<template>
  <section>
    <h1>会員リスト</h1>
    <p>全会員の保有ポイントの合計: {{ totalPoints }}</p>
    <OneMember 
      v-for="[id, member] in memberList"
      v-bind:key="member.id"
      v-bind:id="member.id"
    />
  </section>
</template>

<style scoped>
section {
  border: orange 1px dashed;
  margin: 10px;
}
</style>