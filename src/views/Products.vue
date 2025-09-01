<template>
  <div class="container products">

    <!-- Search + Sort + Category -->
    <div class="row align-items-center mb-4 g-3">
      <!-- Search -->
      <div class="col-md-4">
        <div class="input-group input-group-lg search-bar">
          <span class="input-group-text">
            <i class="bi bi-search"></i>
          </span>
          <input 
            v-model="search" 
            type="text" 
            class="form-control" 
            placeholder="Search products..." />
        </div>
      </div>

      <!-- Sort -->
      <div class="col-md-4">
        <select v-model="sortOption" class="form-select form-select-lg fancy-select">
          <option value="">Sort by</option>
          <option value="asc">Price: Low → High</option>
          <option value="desc">Price: High → Low</option>
        </select>
      </div>

      <!-- Category -->
      <div class="col-md-4">
        <select v-model="selectedCategory" class="form-select form-select-lg fancy-select">
          <option value="">All Categories</option>
          <option v-for="cat in categories" :key="cat" :value="cat">{{ cat }}</option>
        </select>
      </div>
    </div>

    <!-- Alert -->
    <div 
      v-if="alertMessage" 
      class="alert alert-success alert-dismissible fade show" 
      role="alert">
      {{ alertMessage }}
      <button 
        type="button" 
        class="btn-close" 
        @click="alertMessage = ''">
      </button>
    </div>

    <!-- Products grid -->
    <div class="row">
      <div 
        v-for="product in finalProducts" 
        :key="product.id" 
        class="col-md-4 mb-4">
        <div class="card h-100 product-card">
          <img 
            :src="product.image" 
            class="card-img-top p-3" 
            style="height: 250px; object-fit: contain" />
          <div class="card-body d-flex flex-column">
            <h5 class="card-title">{{ product.title }}</h5>
            <p class="card-text fw-bold text-success">
              ${{ product.price }}
            </p>
            <button 
              class="btn fancy-btn mt-auto" 
              @click="addToCart(product)">
              <i class="bi bi-cart-plus me-2"></i> Add to Cart
            </button>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import cartStore from '../cartStore'   // ✅ استدعاء الـ store

const products = ref([])
const search = ref('')
const sortOption = ref('')
const selectedCategory = ref('')
const alertMessage = ref('')
const categories = ref([])

const { addToCart } = cartStore   // ✅ خد الفنكشن من الـ store

// فلترة المنتجات
const filteredProducts = computed(() =>
  products.value.filter(p =>
    p.title.toLowerCase().includes(search.value.toLowerCase()) &&
    (selectedCategory.value ? p.category === selectedCategory.value : true)
  )
)

// ترتيب
const finalProducts = computed(() => {
  let sorted = [...filteredProducts.value]
  if (sortOption.value === 'asc') {
    sorted.sort((a, b) => a.price - b.price)
  } else if (sortOption.value === 'desc') {
    sorted.sort((a, b) => b.price - a.price)
  }
  return sorted
})

// تحميل المنتجات
onMounted(async () => {
  const res = await fetch('https://fakestoreapi.com/products')
  products.value = await res.json()
  categories.value = [...new Set(products.value.map(p => p.category))]
})

// ✅ دالة إضافة للكارت
function handleAdd(product) {
  addToCart(product)
  alertMessage.value = `${product.title} added to cart ✅`
}
</script>

<style>
.products {
  margin-top: 120px; /* تعويض الـ navbar */
}

/* ====== Product Card ====== */
.product-card {
  transition: transform 0.3s, box-shadow 0.3s;
  border: none;
  box-shadow: 0 4px 8px rgba(0,0,0,0.08);
  background: #fff;
}
.product-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 8px 18px rgba(0,0,0,0.15);
}

/* ====== Fancy Button ====== */
.fancy-btn {
  background: linear-gradient(45deg, #0d6efd, #01a181);
  border: none;
  border-radius: 12px;
  color: #fff;
  font-weight: 500;
  padding: 10px 20px;
  transition: all 0.3s ease-in-out;
}
.fancy-btn:hover {
  background: linear-gradient(45deg, #01a181, #0d6efd);
  transform: translateY(-3px);
  box-shadow: 0 6px 12px rgba(13, 110, 253, 0.4);
}
.fancy-btn:active {
  transform: scale(0.95);
}

/* ====== Fancy Select ====== */
.fancy-select {
  border-radius: 12px;
  border: 2px solid #ddd;
  transition: all 0.3s ease-in-out;
}
.fancy-select:focus {
  border-color: #0d6efd;
  box-shadow: 0 0 12px rgba(13, 110, 253, 0.3);
}

/* ====== Search Input ====== */
.search-bar .form-control {
  border-radius: 12px;
  border: 2px solid #ddd;
  transition: all 0.3s ease-in-out;
  font-size: 1.05rem;
  padding: 10px 15px;
}
.search-bar .form-control:focus {
  border-color: #0d6efd;
  box-shadow: 0 0 12px rgba(13, 110, 253, 0.4);
}
.search-bar .input-group-text {
  background: #01a181;
  color: #fff;
  border: none;
  border-radius: 12px 0 0 12px;
  font-size: 1.2rem;
}
</style>
