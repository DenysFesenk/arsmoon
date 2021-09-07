<template>
  <div class="home">
    <ul class="home__list" v-if="contents && contents.objects">
      <li class="home__item" v-for="(content, index) in contents.objects " :key="index">
        <h5 class="home__position">{{ content.position }}</h5>
        <span class="home__employmentType">Employment: {{ content.employmentType }}</span>
        <span class="home__status">Status: {{ content.status}}</span>
        <span class="home__experience">Experience: {{ content.experience }}</span>
        <span class="home__role">Role: {{ content.role }}</span>
        <span class="home__salaryFrom">SalaryFrom: {{ content.salaryFrom }}</span>
        <span class="home__salaryTo">SalaryTo: {{ content.salaryTo }}</span>
        <span class="home__currency">Currency: {{ content.currency }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      contents: null,
      errored: false,
    };
  },
  mounted() {
    axios
      .get("http://localhost:8086/hr/public/getVacancies?alias=staffingpartner")
      .then((response) => (this.contents = response.data))
      .catch((error) => console.log(error));
      
  },
};
</script>

<style lang="scss">
.home {
  padding: 20px 25px;
  display: flex;
  justify-content: center;
  font-size: 18px;
  &__item{
    max-width: 700px;
    border: 1px solid #ccc;
    padding: 20px;
    display: flex;
    flex-direction: column;
    background-color: #f5f5f5;
    cursor: pointer;
    &:not(last-child){
      margin-bottom: 30px;
    }
  }
  &__position{
    color: #1eabce;
    font-size: 24px;
  }
}
</style>
