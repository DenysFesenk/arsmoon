<template>
  <div class="details">
    <ul class="details__list" v-if="contents && contents.objects">
      <li class="details__item" v-for="(content, index) in contents.objects " :key="index">
        <h5 class="details__position">{{ content.position }}</h5>
        <span class="details__employmentType">Employment: {{ content.employmentType }}</span>
        <span class="details__status">Status: {{ content.status}}</span>
        <span class="details__experience">Experience: {{ content.experience }}</span>
        <span class="details__role">Role: {{ content.role }}</span>
        <span class="details__salaryFrom">SalaryFrom: {{ content.salaryFrom }}</span>
        <span class="details__salaryTo">SalaryTo: {{ content.salaryTo }}</span>
        <span class="details__currency">Currency: {{ content.currency }}</span>
        <span class="details__descr" v-html="content.descr" ></span>
        <span class="details__languages" v-if="content.region">Languages: {{ content.region.lang }}</span>
        <span class="details__clientName">Client Name: {{ content.clientName }}</span>
        <!-- <span class="details__clientName">desiredSkills: {{ content.desiredSkills }}</span> -->
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Details",
  data() {
    return {
      contents: '',
      errored: false,
    };
  },
  // computed: {
  //   clearContent: function() {
  //     return this.content.replace(/(<([^>]+)>)/g, "")
  //   }
  // },
  mounted() {
    axios
      .get("http://localhost:8086/hr/public/getVacancies?alias=staffingpartner")
      .then((response) => (this.contents = response.data))
      .catch((error) => console.log(error));  
  },
};
</script>

<style lang="scss">
  .details {
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
