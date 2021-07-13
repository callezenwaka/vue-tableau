<template>
  <div class="header">
    <div class="header--logo">Vue-Tableau</div>
    <div class="header--topics">
      <select v-model="topic" name="topic" id="topic" @change="setTopic">
        <option disabled value="">Please select Topic</option>
        <option :value="topic" v-for="topic in topics" :key="topic.name">{{ topic .name}}</option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: ["topics"],
  data() {
    return {
      topic: "",
    };
  },
  methods: {
    setTopic() {
      this.$emit("setTopic", this.topic);
    },
  },
};
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  min-height: 4rem;
  /* width: 100%; */
  padding-right: 2rem;
}
.header--logo {
  flex: auto;
}
.header--topics select {
  line-height: 1.5;
  min-height: 1.5rem;
  padding: 0 0.5rem;
}
</style>
