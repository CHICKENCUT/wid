<template>
    <div class="photo-widget">
      <h2>Photo Widget</h2>
      <div class="photo-container">
        <img :src="photoUrl" alt="Random Photo" v-if="photoUrl" @click="toggleImageSize" :class="{ 'enlarged': isEnlarged }" />
        <div v-else class="loading-indicator">Memuat...</div>
        <button @click="getRandomPhoto" :disabled="loading">Dapatkan Foto Acak</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        photoUrl: '',
        loading: false,
        isEnlarged: false,
      };
    },
    methods: {
      getRandomPhoto() {
        this.loading = true;
        fetch('https://source.unsplash.com/random')
          .then(response => {
            this.photoUrl = response.url;
            this.loading = false;
          })
          .catch(error => {
            console.error(error);
            this.loading = false;
          });
      },
      toggleImageSize() {
        this.isEnlarged = !this.isEnlarged;
      },
    },
  };
  </script>
  
  <style scoped>
  .photo-widget {
    text-align: center;
  }
  
  .photo-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
  }
  
  img {
    width: 300px;
    height: 300px;
    object-fit: cover;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    transition: transform 0.3s ease;
    cursor: pointer;
  }
  
  img:hover {
    transform: scale(1.05);
  }
  
  img.enlarged {
    transform: scale(1.2);
    z-index: 999;
    position: relative;
  }
  
  .loading-indicator {
    margin-top: 20px;
    font-size: 16px;
    color: #ffffff;
  }
  
  button {
    margin-top: 15px;
    margin-bottom: 13px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: #2196f3;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }
  </style>
  