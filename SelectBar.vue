<template>
  <div class="select-bar mt-xs-10">
    <div class="select-bar__chosen" @click="showOptionsMenu =! showOptionsMenu">
      <span>{{ activeOption ? activeOption : placeholder }}</span>
      <svg xmlns="http://www.w3.org/2000/svg"
           width="10.031"
           height="6"
           fill="#4a67b2"
           style="padding-left: 2px;"
           viewBox="0 0 10.031 6">
        <path id="arrow"
              class="cls-1"
              d="M9.334,12.911l3.848,3.763a1.179,
                1.179,0,0,0,1.631,0l3.849-3.763a1.1,
                1.1,0,0,0,0-1.584,1.164,1.164,
                0,0,0-1.62,0L14,14.3l-3.044-2.976a1.164,
                1.164,0,0,0-1.62,0,1.1,1.1,0,0,0,0,1.584"
              transform="translate(-9 -11)" />
      </svg>
    </div>
    <div class="select-bar__open" v-if="showOptionsMenu">
      <div v-for="(option, index) in selectOptions"
           :key="index"
           @click="chooseOption(option)"
           class="select-bar__open__option">
        {{ option.value }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['selectOptions', 'selectPlaceholder'],
  data() {
    return {
      showOptionsMenu: false,
      activeOption: '',
      placeholder: this.selectPlaceholder,
    };
  },
  methods: {
    chooseOption(optionValue) {
      this.activeOption = optionValue.value;
      this.$emit('chooseProvider', optionValue.id);
      this.showOptionsMenu = false;
    },
  },
};
</script>

<style lang="scss" scoped>
  .select-bar {
    display: inline-block;
    width: 270px;
    &__chosen {
      color: #b0b0b0;
      display: inline-block;
      text-align: left;
      cursor: pointer;
      background: #27264b;
      border-radius: 22px;
      padding: 6px 10px;
      position: relative;
      z-index: 2;
      width: 272px;
      text-transform: capitalize;
      & > svg {
        float: right;
        margin-top: 7px;
        margin-right: 5px;
      }
    }
    &__open {
      width: 271px;
      background: #4a67b2;
      position: absolute;
      top: 62%;
      left: 0;
      text-align: center;
      display: inline-block;
      color: #b0b0b0;
      border-color: #27264b;
      padding-top: 20px;
      z-index: 1;
      border-radius: 4px;
      text-transform: capitalize;
      & > div {
        padding: 2px 0;
      }
    }
    &__open > div:hover {
      color: #fbe412;
      cursor: pointer;
    }
    &__option {
      position: absolute;
      top: 0;
      cursor: pointer;
      display: block;
    }
  }
</style>

