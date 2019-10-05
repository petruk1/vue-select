<template>
  <div class="mdc-select">
    <i class="mdc-select__dropdown-icon"></i>
    <select class="mdc-select__native-control"
            :selected="selection">
      <option v-if="!selection"
              selected
              disabled></option>
      <option v-for="(option, index) of options"
              :key="index"
              :value="option.id">{{option.name}}
      </option>
    </select>
    <label class="mdc-floating-label">{{label}}</label>
    <div class="mdc-line-ripple"></div>
  </div>
</template>

<script>
import { MDCSelect } from '@material/select';

export default {
  name: 'MatSelect',
  props: {
    selection: Number,
    options: Array,
    label: {
      type: String,
      default: '',
    },
    placeholder: {
      type: String,
      default: '',
    },
  },
  model: {
    prop: 'selection',
    event: 'change',
  },
  mounted() {
    const select = new MDCSelect(document.querySelector('.mdc-select'));

    select.listen('MDCSelect:change', (e) => {
      this.$emit('change', parseInt(e.detail.value, 10));
    });
  },
};
</script>

<style scoped>
  @import "~@material/select/dist/mdc.select.min.css";
</style>
