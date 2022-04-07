<template>
  <div id="app">
    <vue-dadata
      ref="dadata"
      :token="token"
      @handle-error="handleError"
      input-name="vue-dadata"
      from-bound="region"
      to-bound="house"
      highlight-class-name="vue-dadata__highlight"
      unhighlight-class-name="vue-dadata__unhighlight"
      highlight-tag="span"
      :on-change="changed"
      :location-options="locations"
      :onFetch="this.testCallback"
      :restrictValue="false"
    ></vue-dadata>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Ref } from 'vue-property-decorator';
import VueDadata from '@/components/VueDadata.vue';

@Component({
  name: 'App',
  components: {
    'vue-dadata': VueDadata,
  },
})
export default class App extends Vue {
  public token = '50ec6ae0336b066a08c6153c6f4c4762fd42d187';
  public locations = {
    language: 'ru',
    locations: [
      // {
      //   region: 'москва',
      // },
      {
        country: '*',
      },
    ],
  };

  @Ref('dadata') readonly dadata!: any;

  public created() {
    this.token = '50ec6ae0336b066a08c6153c6f4c4762fd42d187';
  }

  // public handleBlur() {
  //   this.dadata.setInputQuery('new');
  // }

  public handleError(error: Error) {
    // tslint:disable-next-line:no-console
    // console.log(error);
  }

  public changed(payload: any) {
    // console.log('payload', payload);
  }

  public testCallback (suggestions: object) {
    return suggestions
  }
}
</script>

<style lang="scss">
#app {
}

.vue-dadata__highlight {
  background-color: yellow;
  opacity: 0.2;
}
</style>
