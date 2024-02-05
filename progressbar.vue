<template>
  <div class="progress-bar-wrapper" v-if="progressData">
    <div
      v-for="(step, index) in progressData.stepNumber"
      :key="index"
      class="wrapper"
    >
      <div class="circle-with-tick" v-if="progressData.currentStep < step">
        {{ step }}
      </div>
      <div v-else class="tick-img">
        <img src="@/assets/images/GreenCheckMark.svg" alt="" />
      </div>
      <div
        v-if="index !== progressData.stepNumber - 1"
        class="line-between"
      ></div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  progressData: {
    type: Object,
    required: true,
  },
});

const stepNumber = ref(null);

const currentStep = ref(null);
</script>




<style scoped lang="scss">
.progress-bar-wrapper {
  display: flex;
  width: 100%;
  justify-content: space-between;
  .wrapper {
    display: flex;
    align-items: center;
    flex-grow: 1;
    .tick-img {
      height: 42px;
      width: 42px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .circle-with-tick {
      //   padding: 0.5rem 0.8rem;
      height: 42px;
      width: 42px;
      display: flex;
      justify-content: center;
      align-items: center;
      border: 1px solid #e2e8f0;
      border-radius: 50%;
    }
    .line-between {
      width: 100%;
      height: 2px;
      background-color: #e2e8f0; // set a background color
    }
    &:last-child {
      flex-grow: 0; // Makes the last element not take up remaining space
    }
  }
}
</style>
