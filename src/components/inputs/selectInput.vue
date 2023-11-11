<template>
  <div
    class="form-group form-inline"
    style="white-space: nowrap; font-size: small"
  >
    <label
      :for="id"
      class="text-light justify-content-start"
      style="user-select: none; white-space: pre"
      >{{ text }}</label
    >
    <multiselect
      ref="select"
      v-bind:disabled="disabled !== undefined ? disabled : false"
      v-model="value"
      :options="options"
      @input="$emit('input', $event)"
      :value="value"
      :id="id"
      :show-labels="false"
      :close-on-select="false"
    ></multiselect>
  </div>
</template>

<script>
import Multiselect from "vue-multiselect";

export default {
  name: "selectInput",
  props: ["text", "value", "options", "disabled"],
  components: {
    Multiselect,
  },
  data() {
    return {
      id: null,
    };
  },
  watch: {
    value: {
      handler() {
        if (this.value === "") {
          this.$refs.select.$data.selectedValue = "";
        }
      },
    },
  },
  mounted() {
    this.id = this.uid;
  },
};
</script>

<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>

<style>
.multiselect {
  background-color: var(--bg-secondary) !important;
  color: #f8f9fa !important;
  border-color: var(--brand-primary) !important;
  border-radius: 0.25rem !important;
  border-width: 1px !important;
  border-style: solid !important;
  padding: 0.375rem 0.75rem !important;
  font-size: 1rem !important;
  line-height: 1.5 !important;
  width: 100% !important;
  height: 32px !important;
  margin: 0 !important;
  outline: none !important;
  box-shadow: none !important;
}

.multiselect__single {
  background-color: var(--bg-secondary) !important;
  color: #f8f9fa !important;
  border-color: var(--brand-primary) !important;
  font-size: 1rem !important;
  line-height: 1.5 !important;
  width: 100% !important;
  height: 32px !important;
}

.multiselect__tag:hover {
  background-color: var(--bg-secondary) !important;
  color: #f8f9fa !important;
  border-color: var(--brand-primary) !important;
  font-size: 1rem !important;
  line-height: 1.5 !important;
  width: 100% !important;
}

.multiselect__content {
  background-color: var(--bg-secondary) !important;
  color: #f8f9fa !important;
  border-color: var(--brand-primary) !important;
  font-size: 1rem !important;
  line-height: 1.5 !important;
  width: 100% !important;
}

.multiselect__option--disabled {
  background-color: var(--bg-secondary) !important;
  color: #f8f9fa !important;
  border-color: var(--brand-primary) !important;
  font-size: 1rem !important;
  line-height: 1.5 !important;
  width: 100% !important;
}

.multiselect__tags {
  background-color: var(--bg-secondary) !important;
  color: #f8f9fa !important;
  border-color: var(--bg-secondary) !important;
  font-size: 1rem !important;
  line-height: 1.5 !important;
  width: 100% !important;
  height: 32px !important;
}

.multiselect__tag {
  background-color: var(--bg-secondary) !important;
  color: #f8f9fa !important;
  border-color: var(--brand-primary) !important;
  font-size: 1rem !important;
  line-height: 1.5 !important;
  width: 100% !important;
  height: 32px !important;
}

.multiselect__tag:hover {
  background-color: var(--bg-secondary) !important;
  color: #f8f9fa !important;
  border-color: var(--brand-primary) !important;
  font-size: 1rem !important;
  line-height: 1.5 !important;
  width: 100% !important;
  height: 32px !important;
}

.select-wrapper {
  width: 100% !important;
  height: 32px !important;
}

/*Scroll bar css style for the select overflow*/
/* width */
.select-wrapper ::-webkit-scrollbar {
  width: 5px;
}

/* Track */
.select-wrapper ::-webkit-scrollbar-track {
  background: var(--bg-tertiary);
}

/* Handle */

.select-wrapper ::-webkit-scrollbar-thumb {
  background: var(--brand-primary);
  border-radius: 5px;
}

/*override over the default V select css */
.select-wrapper .v-select-toggle {
  background-color: var(--bg-secondary) !important;
  border-color: var(--brand-primary) !important;
  color: #f8f9fa !important;
}

.select-wrapper .v-select-toggle:hover {
  background-color: var(--bg-secondary) !important;
  border-color: var(--brand-primary) !important;
  color: #f8f9fa !important;
}

.select-wrapper .v-select-toggle:focus {
  background-color: var(--bg-secondary) !important;
  border-color: var(--brand-primary) !important;
  color: #f8f9fa !important;
  outline-color: var(--brand-secondary) !important;
}

.select-wrapper .v-dropdown-container {
  max-height: 40vmin;
  overflow-y: auto;
  overflow-x: hidden;
  background-color: var(--bg-secondary) !important;
}

.select-wrapper .v-dropdown-item {
  text-overflow: ellipsis;
  overflow-x: hidden;
  background-color: var(--bg-secondary) !important;
  color: #f8f9fa !important;
}

.select-wrapper .v-dropdown-item:hover {
  background-color: var(--brand-primary) !important;
}
.disabled .v-select-toggle {
  background-color: var(--bg-tertiary) !important;
  opacity: 1 !important;
  pointer-events: none !important;
}
</style>
