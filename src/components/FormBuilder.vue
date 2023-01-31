<template>
  <div>
        <div v-for="(field, key) in config" :key="key">
        <label>{{field.label}}</label>
      <component
        :is="field.type"
        :name="field.name"
        :params="field.params"
        @input="updateField(field.name, $event)"
        v-validate="field.validation"
        :data-vv-as="field.label"
      >
      </component>
      <span>{{errors.first(field.name)}}</span>
    </div>
    <div>
        <button type="submit" @click="clickMethod()">Submit</button>
    </div>
  </div>
</template>
<script>
import Config from '../form.json'
import InputComponent from './Input.vue'
import CheckboxComponent from './Checkbox.vue'
import RadioButtonComponent from './RadioButton.vue'
import Vue from 'vue'

export default {
  data() {
    return {
      formValues: {},
      config: Config
    };
  },
  created() {
    this.config.map((f) => {
      Vue.set(this.formValues, f.name, null);
    });
  },
  methods:{
      updateField(field, value){
          this.formValues[field]= value
      },
      clickMethod(){
          this.$validator.validate().then(valid => {
        if (!valid) {
          console.log('hi');
        }else{
            console.log('yay');
        }
      });
      }
  },
  components:{
      InputComponent,
      CheckboxComponent,
      RadioButtonComponent,
  }
};
</script>
<style scoped>
</style>