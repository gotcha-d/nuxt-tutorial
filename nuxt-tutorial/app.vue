<script setup lang="ts">
import TheBaseSection from './components/TheBaseSection.vue';
import type { Member } from './interfaces';

// memberListをステートとして用意
// コンポーネントを跨いで利用できるリアクティブデータとして扱える
useState<Map<number, Member>>(
  "memberList",
  (): Map<number, Member> => {
    const memberList = new Map<number, Member>()
    memberList.set(33456, {id: 33456, name: "田中太郎", email: "test@mail.jp", points: 35, note: "初回入会特典あり"})
    memberList.set(47783, {id: 47783, name: "鈴木次郎", email: "test+2@mail.jp", points: 53})
    return memberList
  }
)
</script>
<template>
  <header>
    <h1>ルーティングサンプル</h1>
  </header>
  <main>
    <NuxtPage />
  </main>
</template>

<style>
main {
  border: blue 1px solid;
  padding: 10px;
}

#breadcrumbs ul li {
  display: inline;
  list-style: none;
}

#breadcrumbs {
  margin-left: 0px;
}

#breadcrumbs ul {
  padding-left: 0px;
}

#breadcrumbs ul .current {
  color: red;
}

#breadcrumbs ul li::before {
  content: ">"
}

#breadcrumbs ul li:first-child::before {
  content: none
}
</style>
