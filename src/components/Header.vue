<template>
  <header class="header">
    <div class="header__content">
      <nav class="nav-primary">
        <div class="container">
          <ul class="nav-primary__list">
            <li>
              <a href="#">
                <img src="images/location.svg" alt="location-icon" />
                <span>Волгоградская область</span>
              </a>
            </li>
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
        <div class="container">
          <img src="images/logo.svg" alt="logo" class="logo" />
          <div class="catalog">
            <img src="images/burger.svg" alt="burger" />
            <span>Каталог</span>
          </div>
          <div class="search">
            <input type="search" class="search__input" placeholder="Хочу найти..."/>
            <img src="images/search.svg" alt="search-icon" />
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
