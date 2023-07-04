<template>
  <div class="app">
    <nav>
      <ul>
        <li>
          <router-link to="/tictactoe" class="nav-link" :class="{ 'active': $route.path === '/tictactoe' }">Tic Tac Toe</router-link>
        </li>
        <li>
          <router-link to="/stopwatch" class="nav-link" :class="{ 'active': $route.path === '/stopwatch' }">Stopwatch</router-link>
        </li>
        <li>
          <router-link to="/photo" class="nav-link" :class="{ 'active': $route.path === '/photo' }">Foto</router-link>
        </li>
        <li>
          <router-link to="/location" class="nav-link" :class="{ 'active': $route.path === '/location' }">Lokasi</router-link>
        </li>
        <li>
          <router-link to="/weather" class="nav-link" :class="{ 'active': $route.path === '/weather' }">Cuaca</router-link>
        </li>
      </ul>
    </nav>
    <div class="content">
      <router-view></router-view>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&family=Quicksand&family=Ubuntu+Condensed&display=swap');

.app {
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  display: grid;
  grid-template-columns: 5fr;
  justify-items: center;
  background: linear-gradient(to bottom right, #e5b620, #616061);
  min-height: 100vh; /* Menjamin tampilan penuh pada layar */
  background-image: url("c.jpg");
}

nav {
  border: 3px solid #000000;
  padding: 1px;
  display: flex;
  justify-content: center;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  border-radius: 10px; /* Menggunakan border-radius untuk memberikan tampilan yang lebih lembut pada kotak navigasi */
}


nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  gap: 10px;
}


nav ul li {
  margin-right: 10px;
  display: flex; /* Mengubah tata letak elemen menu agar lebih responsif */
}

nav ul li a {
  text-decoration: none;
  color: #333;
  padding: 10px 15px; /* Menambahkan ruang padding pada elemen menu */
  transition: transform 0.3s ease, background-color 0.3s ease; /* Menambahkan efek transisi pada transformasi dan perubahan latar belakang */
  border-radius: 5px; /* Menambahkan border-radius pada elemen menu */
}

nav ul li a:hover {
  transform: scale(1.1);
  color: #fff;
  background-color: #ff4081; /* Menggunakan warna latar belakang yang lebih menarik */
}

nav ul li a:active {
  color: #777;
  transform: scale(0.9);
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center; /* Mengatur posisi konten di tengah */
  justify-content: center;
  margin-top: 30px; /* Memberikan sedikit ruang antara navigasi dan konten */
}

.nav-link {
  font-weight: 600;
}


.nav-link:hover {
  color: #fff;
  background: linear-gradient(to bottom right, hwb(254 3% 89%), #2b0967);
}


.nav-link:active {
  color: rgb(0, 0, 0);
  transform: scale(1.1);
}

.active {
  color: #fff;
  background: linear-gradient(to bottom right, #605b5f, #ff16c5);
}


</style>