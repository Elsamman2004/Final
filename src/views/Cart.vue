<template>
  <div class="container cart-page">
    <h2 class="mb-4 fw-bold">🛒 Your Cart</h2>

    <!-- لو الكارت فاضية -->
    <div v-if="cart.items.length === 0" class="alert alert-warning text-center p-4 rounded-3 shadow-sm">
      <span>Your cart is empty.</span>
    </div>

    <!-- المنتجات -->
    <div v-else class="row g-4 mb-5">
      <div
        v-for="item in cart.items"
        :key="item.id"
        class="col-12 col-md-6 col-lg-4"
      >
        <div class="card h-100 shadow-sm border-0 rounded-3">
          <img
            :src="item.image"
            class="card-img-top p-3"
            alt="product image"
            style="height: 200px; object-fit: contain;"
          />
          <div class="card-body d-flex flex-column">
            <h6 class="card-title text-truncate">{{ item.title }}</h6>
            <p class="text-muted mb-2">Price: ${{ item.price }}</p>

            <div class="d-flex align-items-center justify-content-between mb-3">
              <div class="quantity-control">
                <button class="btn btn-sm btn-outline-dark" @click="decreaseQuantity(item.id)">−</button>
                <span class="fw-bold mx-2">{{ item.quantity }}</span>
                <button class="btn btn-sm btn-outline-dark" @click="increaseQuantity(item.id)">+</button>
              </div>
              <span class="fw-bold text-success">${{ (item.price * item.quantity).toFixed(2) }}</span>
            </div>

            <button
              class="btn btn-light text-danger border-0 p-0 mt-auto align-self-start"
              @click="removeFromCart(item.id)"
            >
              <i class="bi bi-trash-fill fs-5"></i>
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- الشريط السفلي -->
    <div v-if="cart.items.length > 0" class="cart-footer shadow-lg">
      <div class="d-flex justify-content-between align-items-center w-100">
        <div>
          <h6 class="mb-0">{{ cart.items.length }} items</h6>
          <small class="text-muted">Subtotal: ${{ totalPrice.toFixed(2) }}</small>
        </div>
        <button class="btn btn-success btn-lg px-4">
          Proceed to Checkout
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import cartStore from '../cartStore'

// cart جاي من store
const { cart, removeFromCart, increaseQuantity, decreaseQuantity } = cartStore

// نحسب الإجمالي
const totalPrice = computed(() =>
  cart.items.reduce((sum, item) => sum + item.price * item.quantity, 0)
)
</script>

<style scoped>
.cart-page {
  padding-top: 100px; 
  padding-bottom: 80px; 
}

.card {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
}

.quantity-control button {
  width: 32px;
  height: 32px;
  font-weight: bold;
}

.cart-footer {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background: #fff;
  padding: 15px 30px;
  border-top: 1px solid #ddd;
  z-index: 1050;
}

.btn-success {
  background-color: #01a181;
  border: none;
}
.btn-success:hover {
  background-color: #018060;
}
</style>
