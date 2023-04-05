<script>
export default {
  props: ["inputField"],
  data: () => ({
    validation: {
      required(v) {
        return !!v || "This field is required";
      },
      emailValidation(v) {
        //This regular expression validates the format of an email address. It checks if the input string matches a pattern that includes a username and a domain name, where the username may consist of any combination of letters, numbers, and special characters except for certain characters such as angle brackets and double quotes, and the domain name may consist of one or more segments separated by periods, with each segment containing letters, numbers, and hyphens.
        const pattern =
          /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        return pattern.test(v) || "Invalid Email";
      },
    },
  }),
};
</script>

<template>
  <v-text-field
    class="form-input"
    v-model="inputField.value"
    :rules="inputField.rules.map((rule) => validation[rule])"
    :type="inputField.type"
    :label="inputField.label"
    :name="inputField.name"
    variant="outlined"
    validate-on="blur"
    hide-details="auto"
  ></v-text-field>
</template>

<style lang="scss">
.form-input:not(.v-input--error){
  .v-field:not(.v-field--focused){
    .v-field__outline__start,.v-field__outline__notch::after,.v-field__outline__notch::before,.v-field__outline__end{
      border-color: var(--border-input-color);
    }
  }
}
.v-field--variant-outlined .v-field__outline__end, .v-field--variant-outlined .v-field__outline__end {
  border-radius: 0 4px 4px 0;
}
.v-field--variant-outlined .v-field__outline__start, .v-field--variant-outlined .v-field__outline__start {
    border-radius: 4px 0 0 4px;
}
</style>
