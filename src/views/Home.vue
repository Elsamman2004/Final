<template>
  <div class="home-container text-center py-5 px-3">
    <div class="hero-section mb-5">
      <h1
        class="mb-3 mt-5 display-4 fw-bold animate_animated animate_fadeInDown brand-title"
      >
        <i class="bi bi-shop-window me-2"></i>
        Welcome to Brand Store
      </h1>
      <p
        class="lead mb-4 animate_animated animatefadeIn animate_delay-1s hero-lead"
      >
        Your one-stop destination for amazing products!
      </p>
      <p
        class="mb-5 fs-5 animate_animated animatefadeIn animate_delay-2s hero-desc"
      >
        Discover our wide range of high-quality products at unbeatable prices.<br />
        From <span class="fw-bold">electronics</span> to
        <span class="fw-bold">fashion</span>, we have everything you need.
      </p>
      <router-link
        to="/products"
        class="btn btn-gradient btn-lg mb-5 shadow-sm px-4 py-2"
      >
        <i class="bi bi-stars me-2"></i>
        Show Our Products
        <i class="bi bi-box-seam ms-2"></i>
      </router-link>
    </div>

    <div class="row justify-content-center g-4 mt-4">
      <div class="col-md-4">
        <div class="feature-card-2 animate_animated animate_fadeInUp">
          <div class="feature-icon mb-3">
            <i class="bi bi-truck-front-fill"></i>
            <i class="bi bi-clock-history ms-1 text-info"></i>
          </div>
          <h5 class="feature-title">Fast Shipping</h5>
          <p class="feature-desc">
            Get your orders delivered quickly with our express shipping service.
          </p>
        </div>
      </div>

      <div class="col-md-4">
        <div
          class="feature-card-2 animate_animated animatefadeInUp animate_delay-1s"
        >
          <div class="feature-icon mb-3">
            <i class="bi bi-shield-lock-fill"></i>
            <i class="bi bi-credit-card-2-front-fill ms-1 text-success"></i>
          </div>
          <h5 class="feature-title">Secure Payment</h5>
          <p class="feature-desc">
            Shop with confidence using our secure payment system.
          </p>
        </div>
      </div>

      <div class="col-md-4">
        <div
          class="feature-card-2 animate_animated animatefadeInUp animate_delay-2s"
        >
          <div class="feature-icon mb-3">
            <i class="bi bi-headset"></i>
            <i class="bi bi-chat-dots-fill ms-1 text-primary"></i>
          </div>
          <h5 class="feature-title">24/7 Support</h5>
          <p class="feature-desc">
            Our customer support team is here to help you anytime.
          </p>
        </div>
      </div>
    </div>

    <div
      class="trusted-section mt-5 animate_animated animatefadeInUp animate_delay-3s"
    >
      <h4 class="mb-4 trusted-title">Trusted by 10,000+ happy customers</h4>
      <div class="d-flex justify-content-center gap-4 flex-wrap">
        <i class="bi bi-star-fill text-star fs-3"></i>
        <i class="bi bi-star-fill text-star fs-3"></i>
        <i class="bi bi-star-fill text-star fs-3"></i>
        <i class="bi bi-star-fill text-star fs-3"></i>
        <i class="bi bi-star-half text-star fs-3"></i>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css";

.home-container {
  background: #0a0a0a;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.brand-title {
  color: #fff;
  text-shadow: 0 2px 12px rgba(30, 60, 114, 0.25);
}

.brand-gradient {
  background: linear-gradient(90deg, #ffd700 0%, #ff9900 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-fill-color: transparent;
  font-weight: bold;
}

.hero-lead {
  color: #e0f7fa;
  text-shadow: 0 1px 6px rgba(56, 239, 125, 0.12);
}

.hero-desc {
  color: #f8f9fa;
  text-shadow: 0 1px 6px rgba(56, 239, 125, 0.1);
}

/* Pulse Animation */
@keyframes pulseGlow {
  0% {
    transform: scale(1);
    box-shadow: 0 0 0 rgba(255, 204, 51, 0);
  }
  50% {
    transform: scale(1.05);
    box-shadow: 0 0 20px rgba(255, 204, 51, 0.6);
  }
  100% {
    transform: scale(1);
    box-shadow: 0 0 0 rgba(255, 204, 51, 0);
  }
}

.btn-gradient {
  background: linear-gradient(90deg, #ffb347 0%, #ffcc33 100%);
  color: #222;
  border: none;
  font-weight: bold;
  transition: box-shadow 0.25s ease, transform 0.25s ease;
  animation: pulseGlow 2s infinite;
}
.btn-gradient:hover {
  background: linear-gradient(90deg, #ffcc33 0%, #ffb347 100%);
  color: #111;
  transform: translateY(-3px) scale(1.07);
}

.text-highlight {
  color: #ffeb3b;
  background: linear-gradient(90deg, #ffd700 0%, #ff9900 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-fill-color: transparent;
}

.feature-card-2 {
  border-radius: 22px;
  box-shadow: 0 4px 32px 0 rgba(30, 60, 114, 0.1),
    0 1.5px 8px 0 rgba(56, 239, 125, 0.1);
  padding: 2.2rem 1.5rem 1.5rem 1.5rem;
  transition: transform 0.3s, box-shadow 0.3s, background 0.3s;
  border: none;
  position: relative;
  overflow: hidden;
}
.feature-card-2:hover {
  background: #01a181;
  transform: translateY(-10px);
  box-shadow: 0 0 25px rgba(0, 255, 204, 0.5);
}

.feature-icon {
  font-size: 2.2rem;
  color: #ff9800;
  background: linear-gradient(90deg, #ffd700 0%, #ff9800 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-fill-color: transparent;
  margin-bottom: 0.5rem;
  transition: color 0.3s;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.3em;
}

.feature-title {
  font-size: 1.35rem;
  font-weight: bold;
  color: #1e3c72;
  margin-bottom: 0.7rem;
  letter-spacing: 0.5px;
}

.feature-desc {
  color: #444;
  font-size: 1.08rem;
  font-weight: 500;
  letter-spacing: 0.1px;
}

.trusted-section {
  background-color: black;
  border-radius: 22px;
  box-shadow: 0 4px 32px 0 rgba(30, 60, 114, 0.1),
    0 1.5px 8px 0 rgba(56, 239, 125, 0.1);
  padding: 2.2rem 1.5rem 1.5rem 1.5rem;
  transition: transform 0.3s, box-shadow 0.3s, background 0.3s;
  border: none;
  position: relative;
  overflow: hidden;
}
.trusted-section:hover {
  background: #01a181;
  transform: translateY(-10px);
  box-shadow: 0 0 25px rgba(0, 255, 204, 0.5);
}

.trusted-title {
  color: #fffde7;
  text-shadow: 0 2px 12px rgba(30, 60, 114, 0.18);
}

.text-star {
  color: #ffd700 !important;
  text-shadow: 0 2px 8px rgba(255, 215, 0, 0.18);
}
</style>
