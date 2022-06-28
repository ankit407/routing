<template>
  <section class="vh-100" style="background-color: #f4f6f8">
    <div class="container h-100">
      <div class="row d-flex justify-content-center align-items-center h-100">
        <div class="col-lg-12 col-xl-12">
          <div class="card text-black" style="border-radius: 25px">
            <div class="card-body p-md-8">
              <div class="row justify-content-center">
                <div class="col-md-9 col-lg-8 col-xl-5 order-2 order-lg-1">
                  <p class="text-center h1 fw-bold mb-5 mx-1 mx-md-4 mt-4">
                    User Sign Up
                  </p>

                  <label class="form-label" for="form3Example3c"
                    >Your Email</label
                  >
                  <FormulateInput
                    type="email"
                    v-model="form.email"
                    validation="required|email"
                  />

                  <label class="form-label" for="form3Example3c"
                    >Your Password</label
                  >
                  <FormulateInput
                    type="password"
                    v-model="form.password"
                    validation="required"
                  />

                  <label class="form-label" for="form3Example3c"
                    >Confirm Password</label
                  >
                  <FormulateInput
                   
                    type="password"
                    v-model="form.confirmation"
                    validation="required|confirm"
                  />
                  <br />

                  <button type="submit" name="button" @click="postNow">
                    Submit
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import axios from "axios";

export default {
  data() {
    return {
      form: {
        name: "",
        email: "",
        password: "",
        confirmation: "",
      },
    };
  },
  methods: {
    postNow() {
      var formData = new FormData();
      formData.append("email", this.form.email);
      formData.append("password", this.form.password);
      formData.append("confirmation", this.form.confirmation);
      const axioObj = {
        method: "post",
        url: "/v1/users",
        data: formData,
        headers: {
          "Content-type": "multipart/form-data",
          Authorization: "Bearer eb4a35d1-ca5d-487a-b16e-05598fe7a3bb",
        },
      };
      axios(axioObj);
    },
  },
};
</script>
<style scoped>
</style>