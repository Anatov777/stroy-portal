<template>
  <header class="header">
    <div class="header__content">
      <nav class="nav-primary">
        <div class="content-container">
          <ul class="nav-primary__list">
            <li>
              <a href="#">
                <img src="images/location.svg" alt="location-icon" />
                <span>Волгоградская область</span>
              </a>
            </li>
            <li v-if="!burgerTrigger"><a href="#">Тендеры</a></li>
            <li v-if="!burgerTrigger"><a href="#">База подрядчиков</a></li>
            <li v-if="!burgerTrigger">
              <a href="#">
                <span>Другие сервисы</span>
                <img src="images/arrow-down.svg" alt="arrow-down-icon" />
              </a>
            </li>
            <div
              class="nav-burger"
              v-if="burgerTrigger"
              v-on:click="burgerClick"
              v-bind:class="{ active: burgerActive }"
            >
              <img src="images/burger.svg" alt="nav-burger" />
            </div>
          </ul>
        </div>
        <div class="nav-burger__content" v-if="navBurger">
          <ul>
            <li><a href="#">Тендеры</a></li>
            <li><a href="#">База подрядчиков</a></li>
            <li>
              <a href="#">
                <span>Другие сервисы</span>
                <img src="images/arrow-down.svg" alt="arrow-down-icon" />
              </a>
            </li>
          </ul>
        </div>
      </nav>
      <div class="header__body">
        <div class="content-container">
          <a href="#" class="logo"><img src="images/logo.svg" alt="logo" /></a>
          <div class="catalog">
            <img src="images/burger.svg" alt="burger" />
            <span>Каталог</span>
          </div>

          <div class="search" v-bind:class="{ active: searchModel }">
            <v-autocomplete
              :items="states"
              :filter="customFilter"
              color="#708598"
              item-text="name"
              label="Хочу найти..."
              append-icon=""
              clearable
              hide-details
              solo
              v-model="searchModel"
            ></v-autocomplete>
            <img
              src="images/search.svg"
              alt="search-icon"
              v-if="!searchModel"
            />
          </div>

          <div class="list">
            <div>
              <img src="images/list.svg" alt="burger" />
            </div>
            <span>Список</span>
          </div>
          <div class="profile">
            <span>A</span>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import Vuetify from "vuetify/lib";

export default {
  vuetify: new Vuetify(),
  data() {
    return {
      searchModel: false,
      burgerTrigger: false,
      navBurger: false,
      burgerActive: false,
      states: [
        { name: "Florida", abbr: "FL", id: 1 },
        { name: "Georgia", abbr: "GA", id: 2 },
        { name: "Nebraska", abbr: "NE", id: 3 },
        { name: "California", abbr: "CA", id: 4 },
        { name: "New York", abbr: "NY", id: 5 },
      ],
    };
  },

  created() {
    window.addEventListener("resize", this.handleResize);
    this.handleResize();
  },
  destroyed() {
    window.removeEventListener("resize", this.handleResize);
  },

  methods: {
    handleResize() {
      if (window.innerWidth < 530) {
        this.burgerTrigger = true;
      } else {
        this.burgerTrigger = false;
      }
    },
    customFilter(item, queryText) {
      const textOne = item.name.toLowerCase();
      const textTwo = item.abbr.toLowerCase();
      const searchText = queryText.toLowerCase();

      return (
        textOne.indexOf(searchText) > -1 || textTwo.indexOf(searchText) > -1
      );
    },
    burgerClick() {
      this.navBurger = !this.navBurger;
      this.burgerActive = !this.burgerActive;
    },
  },
};
</script>
