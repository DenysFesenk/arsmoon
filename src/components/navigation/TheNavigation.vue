<template>
  <div class="navi">
    <ul class="navi__list">
      <li class="navi__item" v-for="route in routes" :key="route.name">
        <router-link class="navi__item-link" :to="route.path">
          {{ route.name }}
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "The-navigation",
  data() {
    return {
      value: 2,
      routes: [
        {
          path: "/",
          name: "All vacancies",
        },
        {
          path: "/details",
          name: "More about",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.navi {
    &__list{
        display: flex;
        align-items: center;
        justify-content: center;
    }
    &__item{
        &:not(last-child){
            margin-right: 20px;
        }
    }
    &__item-link {
      font-weight: bold;
      color: #2c3e50;
      border-bottom: 1px solid #2c3e50;

      &.router-link-exact-active {
        color: #b8860b;
        border-bottom: 1px solid #b8860b;
      }
  }
}
</style>
