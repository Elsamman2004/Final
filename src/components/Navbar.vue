<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
      <!-- Brand name -->
      <router-link class="navbar-brand d-flex align-items-center" to="/">
        <i class="bi bi-bag-check-fill me-2"></i>
        Elsamman Store 
      </router-link>

      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarNav">
        <!-- Left side -->
        <ul class="navbar-nav me-auto">
          <li class="nav-item">
            <router-link class="nav-link" to="/">
              <i class="bi bi-house-door-fill me-1"></i> Home
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/products">
              <i class="bi bi-box-seam me-1"></i> Products
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/about">
              <i class="bi bi-info-circle-fill me-1"></i> About
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/contact">
              <i class="bi bi-envelope-fill me-1"></i> Contact
            </router-link>
          </li>
        </ul>

        <!-- Right side: Cart -->
        <ul class="navbar-nav ms-auto">
          <li class="nav-item position-relative">
            <router-link class="nav-link" to="/cart">
              <i class="bi bi-cart-fill me-1"></i> Cart
              <span
                v-if="cartCount > 0"
                key="cart-badge"
                class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger pulse-badge"
                style="font-size: 0.7rem;"
              >
                {{ cartCount }}
              </span>
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { computed } from 'vue'
import cartStore from '../cartStore'

const { cart } = cartStore

const cartCount = computed(() =>
  cart.items.reduce((sum, item) => sum + item.quantity, 0)
)
</script>

<style scoped>
/* Pulse animation للـ badge */
@keyframes pulse {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  50% {
    transform: scale(1.3);
    opacity: 0.8;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

.pulse-badge {
  animation: pulse 0.5s ease;
}
</style>
