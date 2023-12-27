<template>
  <main>
      <ContentDoc v-slot="{ doc }">
        <article>
          <h1>{{ doc.title }}</h1>
          <h2>{{ doc.description }}</h2>
          <h2>{{ doc.date }}</h2>
          <ContentRenderer :value="doc" />
        </article>
      </ContentDoc>
  </main>
  comments
</template>