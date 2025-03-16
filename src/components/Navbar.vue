<script setup lang="ts">
import { ref } from 'vue';
import { RouterLink } from 'vue-router';

const isOpen = ref(false);

const toggleMenu = () => {
  isOpen.value = !isOpen.value;
};

const closeMenu = () => {
  isOpen.value = false;
};
</script>

<template>
  <nav class="navbar">
    <div class="container">
      <RouterLink to="/" class="brand" @click="closeMenu">
        <span>Logan Rivera</span>
      </RouterLink>

      <ul class="nav-links" :class="{ 'active': isOpen }">
        <li><RouterLink to="/" class="nav-link" @click="closeMenu">Home</RouterLink></li>
        <li><RouterLink to="/projects" class="nav-link" @click="closeMenu">Projects</RouterLink></li>
        <li><RouterLink to="/about" class="nav-link" @click="closeMenu">About</RouterLink></li>
        <li><RouterLink to="/contact" class="nav-link" @click="closeMenu">Contact</RouterLink></li>
      </ul>

      <button 
        class="hamburger" 
        :class="{ 'active': isOpen }" 
        @click="toggleMenu"
        aria-label="Toggle navigation menu"
      >
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  z-index: 1000;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.brand {
  font-size: 1.5rem;
  font-weight: 700;
  color: #333;
  text-decoration: none;
  transition: color 0.3s ease;
}

.brand:hover {
  color: #646cff;
}

.nav-links {
  display: flex;
  gap: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-link {
  text-decoration: none;
  color: #333;
  font-weight: 500;
  transition: color 0.3s ease;
  position: relative;
  padding: 0.5rem 0;
}

.nav-link:hover {
  color: #646cff;
}

.nav-link.router-link-exact-active {
  color: #646cff;
}

.nav-link.router-link-exact-active::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 2px;
  background-color: #646cff;
}

.hamburger {
  display: none;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  z-index: 1001;
}

.bar {
  display: block;
  width: 25px;
  height: 2px;
  margin: 5px 0;
  background-color: #333;
  transition: all 0.3s ease;
}

@media (max-width: 768px) {
  .hamburger {
    display: block;
  }

  .hamburger.active .bar:nth-child(1) {
    transform: translateY(7px) rotate(45deg);
  }

  .hamburger.active .bar:nth-child(2) {
    opacity: 0;
  }

  .hamburger.active .bar:nth-child(3) {
    transform: translateY(-7px) rotate(-45deg);
  }

  .nav-links {
    position: fixed;
    top: 70px;
    right: -100%;
    flex-direction: column;
    background: rgba(255, 255, 255, 0.95);
    width: 100%;
    text-align: center;
    transition: right 0.3s ease;
    padding: 2rem 0;
    gap: 1.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .nav-links.active {
    right: 0;
  }

  .nav-link {
    font-size: 1.2rem;
    padding: 0.5rem 1rem;
  }

  .nav-link.router-link-exact-active::after {
    display: none;
  }
}
</style>