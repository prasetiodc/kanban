<template>
  <div>
    <b-card header-tag="header" footer-tag="footer"
    style="width:280px; color: white;" :header-bg-variant="variant">
      <h6 slot="header" class="mb-0">{{ headertest }}</h6>
      <Task v-for="(task, index) in list" :key="index" :detail="task"/>
    </b-card>
  </div>
</template>

<script>
import Task from '@/components/Task.vue';

export default {
  props: ['headertest', 'list', 'variant'],
  name: 'task',
  components: {
    Task,
  },
  data() {
    return {};
  },
};
</script>

<style scoped>
.card {
  margin: 0 10px;
}
.card-body{
  padding: 10px;
}
</style>
