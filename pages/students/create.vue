import { NuxtLink } from '../../.nuxt/components';
<template>
  <div class="mt-5 container">
    <div class="card">
      <div class="card-header">
        <h4>
          Add Student
          <NuxtLink class="btn btn-danger float-end" to="/"> Back</NuxtLink>
        </h4>
      </div>
      <div class="card-body">
        <form @submit.prevent="createAccount" action="">
          <div v-if="isLoading">
          </div>
          <div class="form-group">
            <div class="mb-3">
              <label for="username">Name</label>
              <input
                v-model="student.name"
                type="text"
                id="username"
                class="form-control"
                placeholder="Enter Fullnames"
              />
            </div>
            <div class="form-group">
              <div class="mb-3">
                <label for="course">Course</label>
                <input
                  v-model="student.course"
                  type="text"
                  id="course"
                  class="form-control"
                  placeholder="Enter Course Name"
                />
              </div>
            </div>
            <div class="form-group">
              <div class="mb-3">
                <label for="email">Email</label>
                <input
                  v-model="student.email"
                  type="email"
                  id="email"
                  class="form-control"
                  placeholder="Enter Email Address"
                />
              </div>
            </div>
            <div class="form-group">
              <div class="mb-3">
                <label for="phone">Phone</label>
                <input
                  v-model="student.phone"
                  type="text"
                  id="phone"
                  class="form-control"
                  placeholder="Enter Phone"
                />
              </div>
            </div>
            <div class="form-group">
              <div class="mb-3">
                <label for="password">Password</label>
                <input
                  v-model.lazy="student.password"
                  type="password"
                  id="password"
                  :class="{ pass: !isPassCorrect }"
                  class="form-control"
                  placeholder="Enter Password"
                />
              </div>
            </div>
            <div class="form-group">
              <div class="mb-3">
                <label for="cpassword">Confirm Password</label>
                <input
                  v-model.lazy="student.cpassword"
                  type="password"
                  id="cpassword"
                  :class="{ pass: !isPassCorrect }"
                  class="form-control"
                  placeholder="Confirm Password"
                />
              </div>
            </div>

            <div class="form-group">
              <div class="mb3">
                <button
                  type="submit"
                  class="btn btn-primary"
                  :disabled="!isPassCorrect"
                >
                  Save
                </button>
              </div>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "StudentCreate",
  data() {
    return {
      student: {
        name: "",
        course: "",
        email: "",
        phone: "",
        password: "",
        cpassword: "",
      },
      isPassCorrect: true,
      isLoading: false,
      isLoadingText: "loading...",
    };
  },
  methods: {
    createAccount() {
      this.isLoading = "true";
      this.isLoading = "saving";
      alert(this.student.password);
    },
  },
  computed: {
    isPassCorrect() {
      return this.student.password === this.student.cpassword;
    },
  },
};
</script>

<style scoped>
.pass {
  border: 1px solid red;
  background: #f8d7da;
  color: #721c24 !important;
}
</style>
