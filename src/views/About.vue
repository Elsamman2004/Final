<template>
  <div class="about-page">
    <!-- OUR STORY HERO SECTION -->
    <section class="hero-section d-flex align-items-center text-center text-white">
      <div class="hero-overlay w-100 h-100 d-flex flex-column justify-content-center">
        <div class="container py-5">
          <h6 class="fw-bold text-uppercase fade-down">OUR STORY</h6>
          <h2 class="brand-title fade-up">About  Store</h2>
          <p class="lead mx-auto fade-up-delay">
            Discover the passion, craftsmanship, and vision behind Brand Store's timeless fashion collections.
          </p>
        </div>
      </div>
    </section>

    <!-- Our Story Content -->
    <div class="container my-5">
      <div class="card shadow-lg border-0 p-4 animate_animated animate_fadeInUp soft-card">
        <h2 class="fw-bold mb-3 text-center text-light">Our Story</h2>
        <p class="text-light">
          Brand Store was born from a bold vision: to redefine premium fashion by making it not only accessible, but also inspiring and unforgettable...
        </p>
      </div>
    </div>

    <!-- Our Team -->
    <div class="container my-5">
      <h2 class="text-center fw-bold mb-4 section-title">Our Team</h2>
      <div class="row g-4">
        <div class="col-md-4" v-for="(member, index) in team" :key="index">
          <div class="card team-card text-center p-4 shadow-lg h-100 fade-up glow-hover">
            <i :class="member.icon" class="display-4 mb-3 gradient-text"></i>
            <h5 class="fw-bold text-light">{{ member.title }}</h5>
            <p class="text-muted">{{ member.role }}</p>
            <p>{{ member.desc }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Our Values -->
    <div class="container my-5">
      <h2 class="text-center fw-bold mb-4 section-title">Our Values</h2>
      <div class="row g-4">
        <div class="col-md-4" v-for="(value, index) in values" :key="index">
          <div class="card value-card shadow-lg h-100 p-4 text-center fade-up glow-hover">
            <i :class="value.icon" class="display-4 mb-3 gradient-text"></i>
            <h5 class="fw-bold text-light">{{ value.title }}</h5>
            <p>{{ value.desc }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Craftsmanship & Global Inspiration -->
    <div class="container my-5">
      <div class="row g-4">
        <div class="col-md-6" v-for="(extra, index) in extras" :key="index">
          <div class="card shadow-lg p-4 text-center fade-up glow-hover">
            <i :class="extra.icon" class="display-4 mb-3 gradient-text"></i>
            <h5 class="fw-bold text-light">{{ extra.title }}</h5>
            <p>{{ extra.desc }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const team = [
  { icon: "bi bi-brush", title: "Creative Director", role: "Fashion & Design", desc: "Leads our creative vision..." },
  { icon: "bi bi-megaphone", title: "Brand Manager", role: "Brand Strategy & Marketing", desc: "Develops Brand Store's identity..." },
  { icon: "bi bi-star", title: "Style Curator", role: "Fashion & Trends", desc: "Curates collections and stays ahead of fashion trends..." }
]

const values = [
  { icon: "bi bi-award", title: "Premium Quality", desc: "We source only the finest materials..." },
  { icon: "bi bi-heart", title: "Customer Love", desc: "Every customer is part of the Brand Store family..." },
  { icon: "bi bi-clock-history", title: "Timeless Style", desc: "We create pieces that transcend trends..." }
]

const extras = [
  { icon: "bi bi-scissors", title: "Craftsmanship Excellence", desc: "Every piece is meticulously crafted..." },
  { icon: "bi bi-globe", title: "Global Inspiration", desc: "Our designs are inspired by fashion capitals worldwide..." }
]
</script>

<style scoped>
/* HERO */
.hero-section {
  height: 100vh;
  background: url('https://www.glamorous-design.com/wp-content/uploads/2022/12/%D8%AA%D8%B5%D9%85%D9%8A%D9%85-%D9%85%D8%AD%D9%84-%D9%84%D9%84%D9%85%D9%84%D8%A7%D8%A8%D8%B3.webp') no-repeat center/cover;
  position: relative;
}
.about-page { background: black; }
.hero-overlay {
  background: rgba(0, 0, 0, 0.6);
}
.brand-title {
  font-size: 56px;
  font-family: 'Georgia', serif;
  font-weight: 700;
}
@media (max-width: 768px) {
  .brand-title { font-size: 32px; }
}

/* SECTION TITLES */
.section-title {
  font-size: 38px;
  color: #fff;
  position: relative;
}
.section-title::after {
  content: '';
  width: 70px;
  height: 3px;
  background: #01a181;
  display: block;
  margin: 12px auto 0;
  border-radius: 2px;
}

/* CARDS */
.card {
  background-color: #00120f7e;
  border-radius: 22px;
  padding: 2rem 1.5rem;
  transition: transform 0.3s, box-shadow 0.3s, background 0.3s;
  border: none;
  position: relative;
  overflow: hidden;
}
.card:hover {
  background: #01a181;
  transform: translateY(-10px);
  box-shadow: 0 0 25px rgba(0, 255, 204, 0.5);
}
.glow-hover:hover {
  box-shadow: 0 0 35px rgba(0, 255, 170, 0.7);
}

/* ICONS GRADIENT */
.gradient-text {
  background: linear-gradient(45deg, #00ffcc, #01a181);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
