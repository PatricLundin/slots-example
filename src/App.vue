<template>
  <div id="app">
    <div class="flex-layout">
      <!-- #0 Default without slots -->
      <Container />

      <!-- #1 & #2 Change header/text -->
      <Container title="Changed title" />
      <Container text="Changed text" />

      <!-- #3 Need to change header to h1-->
      <Container>
        <template #header>
          <h1>H1 title</h1>
        </template>
      </Container>

      <!-- #4 Need to change to h1 but use default title -->
      <Container>
        <template #header="{ title }">
          <h1>{{ title }}</h1>
        </template>
      </Container>

      <!-- #5 Change main content  -->
      <Container title="Dual Layout">
        <template #content>
          <DualLayout />
        </template>
      </Container>

      <!-- #6 Change main content nested....  -->
      <Container title="Dual Layout 2">
        <template #content="{ text }">
          <DualLayout :rightText="text">
            <template #left>
              <DualLayout leftText="Nested left dual layout" />
            </template>
          </DualLayout>
        </template>
      </Container>
    </div>
  </div>
</template>

<script>
import Container from './components/Container.vue';
import DualLayout from './components/DualLayout.vue';

export default {
  name: 'App',
  components: {
    Container,
    DualLayout,
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
  background-color: #333;
}

h1, h2, h3, h4, h5, h6, p {
  margin: 0;
}

.flex-layout {
  display: flex;
  flex-wrap: wrap;
}
</style>
