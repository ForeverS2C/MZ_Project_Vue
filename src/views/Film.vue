<template>
  <div>
    <MzBanner></MzBanner>
    <MzTabs></MzTabs>
    <MzFooter></MzFooter>
  </div>
</template>

<script>
import MzBanner from '../components/MzBanner/Index.vue';
import MzFooter from '../components/MzFooter/Index.vue';
import MzTabs from '../components/MzTabs/Index.vue';

export default {
  components: {
    MzBanner,
    MzFooter,
    MzTabs
  }
};
</script>
