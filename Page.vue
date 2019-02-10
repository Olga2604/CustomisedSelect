<template>
  <div>
    <h1>This is an awesome select!</h1>
    <select-bar :selectPlaceholder="'Choose a fruit'"
                :selectOptions="getAllFruits"
                @chooseOption="getChosenOption"/>
  </div>
</template>

<script>
import SelectBar from '../../elements/SelectBar';


export default {
  components: { SelectBar },
  ...
  methods: {
    getChosenOption(value) {
      return value;
    },
  },
};
</script>
