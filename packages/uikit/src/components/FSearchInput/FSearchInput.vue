<template>
  <f-input
    :placeholder="text.search"
    :value="value"
    class="f-search-input"
    v-bind="$attrs"
    v-on="$listeners"
  >
    <template #prepend-inner>
      <v-icon color="greyscale_4">$search</v-icon>
    </template>
  </f-input>
</template>

<script lang="ts">
import { Component, Model, Vue, Prop } from "vue-property-decorator";
import { VIcon } from "vuetify/lib";
import FInput from "../FInput";
import { $t } from "../../utils/helper";

@Component({
  name: "FSearchInput",
  components: {
    VIcon,
    FInput
  }
})
class FSearchInput extends Vue {
  @Model("input") value!: string;

  @Prop({ type: String, default: "" }) placeholder!: string;

  get text() {
    return { search: this.placeholder || $t(this, "search") };
  }
}
export default FSearchInput;
</script>

<style lang="scss" scoped>
.v-input--is-dirty,
.v-input--is-focused {
  ::v-deep {
    .v-input__prepend-inner {
      opacity: 0;
      width: 0;
      padding-right: 0 !important;
    }
  }
}

::v-deep {
  .v-input__prepend-inner {
    transition: 0.1s ease;
  }
}
</style>
