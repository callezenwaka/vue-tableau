<template>
  <div class="home">
    <Header :topics="topics" @setTopic="setTopic"></Header>
    <div class="home--wrapper">
      <div ref="tableau"></div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from "@/components/Header.vue";
export default {
  name: "Home",
  components: {
    Header,
  },
  data() {
    return {
      topics: [
        {
          id: 1,
          name: "Obesity",
          url: "https://public.tableau.com/views/RegionalSampleWorkbook/Obesity?:language=en-US&:display_count=n&:origin=viz_share_link",
          options: { hideTabs: true },
        },
        {
          id: 2,
          name: "College",
          url: "https://public.tableau.com/views/RegionalSampleWorkbook/College?:language=en-US&:display_count=n&:origin=viz_share_link",
          options: { hideTabs: true },
        },
        {
          id: 3,
          name: "Economy",
          url: "https://public.tableau.com/views/RegionalSampleWorkbook/Economy?:language=en-US&:display_count=n&:origin=viz_share_link",
          options: { hideTabs: true },
        },
        {
          id: 4,
          name: "Stocks",
          url: "https://public.tableau.com/views/RegionalSampleWorkbook/Stocks?:language=en-US&:display_count=n&:origin=viz_share_link",
          options: { hideTabs: true },
        },
        {
          id: 5,
          name: "Storms",
          url: "https://public.tableau.com/views/RegionalSampleWorkbook/Storms?:language=en-US&:display_count=n&:origin=viz_share_link",
          options: { hideTabs: true },
        },
        {
          id: 6,
          name: "Flights",
          url: "https://public.tableau.com/views/RegionalSampleWorkbook/Flights?:language=en-US&:display_count=n&:origin=viz_share_link",
          options: { hideTabs: true },
        },
      ],
    };
  },
  mounted() {
    this.initViz(this.topics[0]);
  },
  methods: {
    setTopic(topic) {
      this.initViz(topic);
    },
    initViz(topic) {
      let viz = window.tableau.VizManager.getVizs()[0];
      if (viz) {
        viz.dispose();
      }
      // eslint-disable-next-line no-undef
      viz = new tableau.Viz(this.$refs.tableau, topic.url, topic.options);
      return viz;
    },
  },
};
</script>

<style scoped>
.home {
  padding: 0;
  margin: 0;
}
.home--wrapper {
  padding: 1rem;
}
</style>
