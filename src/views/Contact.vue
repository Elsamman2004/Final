<template>
  <div class="contact-page py-5 ">
    <div class="container contact-home">
      <!-- TITLE -->
      <h2 class="text-center fw-bold mb-5 section-title">📩 Contact Us</h2>

      <!-- INFO CARDS -->
      <div class="row text-center mb-5">
        <div class="col-md-4 mb-4">
          <div class="info-card shadow">
            <i class="fas fa-map-marker-alt fa-2x mb-3"></i>
            <h5 class="fw-bold">Your Location</h5>
            <p class="text-light">Suez , Egypt</p>
          </div>
        </div>
        <div class="col-md-4 mb-4">
          <div class="info-card shadow">
            <i class="fas fa-phone fa-2x mb-3"></i>
            <h5 class="fw-bold">Call Us</h5>
            <p>
              <a href="tel:+201112285662">+20 111 228 5662</a>
            </p>
          </div>
        </div>
        <div class="col-md-4 mb-4">
          <div class="info-card shadow">
            <i class="fas fa-envelope fa-2x mb-3"></i>
            <h5 class="fw-bold">Email</h5>
            <p>
              <a href="mailto:mohammed511yasser@gmail.com">
                mohammed511yasser@gmail.com
              </a>
            </p>
          </div>
        </div>
      </div>

      <!-- GOOGLE MAP -->
      <div class="map-container mb-5">
        <iframe
          class="map"
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d55297.32117951782!2d32.55269463872721!3d29.977056838849066!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x1456257838ae4111%3A0x1f0a056a97ea1bc0!2z2KfZhNiz2YjZitiz2Iwg2YXYrdin2YHYuNipINin2YTYs9mI2YrYsw!5e0!3m2!1sar!2seg!4v1756687694507!5m2!1sar!2seg"
          width="100%"
          height="400"
          style="border: 0"
          allowfullscreen=""
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
        ></iframe>
      </div>

      <!-- SUCCESS MESSAGE -->
      <div v-if="success" class="alert-card success-card fade-in">
        ✅ Thank you for contacting us! We'll get back to you soon.
      </div>

      <!-- FORM -->
      <div class="card shadow-lg p-4 form-card">
        <form @submit.prevent="submitForm">
          <!-- NAME -->
          <div class="mb-3">
            <label class="form-label text-light">Name</label>
            <input
              v-model="form.name"
              type="text"
              class="form-control input-custom"
              placeholder="Enter your name"
            />
            <div v-if="errors.name" class="text-danger small">
              {{ errors.name }}
            </div>
          </div>

          <!-- EMAIL -->
          <div class="mb-3">
            <label class="form-label text-light">Email</label>
            <input
              v-model="form.email"
              type="email"
              class="form-control input-custom"
              placeholder="Enter your email"
            />
            <div v-if="errors.email" class="text-danger small">
              {{ errors.email }}
            </div>
          </div>

          <!-- MESSAGE -->
          <div class="mb-3">
            <label class="form-label text-light">Message</label>
            <textarea
              v-model="form.message"
              rows="4"
              class="form-control input-custom"
              placeholder="Write your message..."
            ></textarea>
            <div v-if="errors.message" class="text-danger small">
              {{ errors.message }}
            </div>
          </div>

          <!-- SUBMIT -->
          <button type="submit" class="btn btn-submit w-100 mt-3">
            Send Message
          </button>
        </form>
      </div>

      <!-- SOCIAL ICONS AT BOTTOM -->
      <div class="social-footer">
        <a href="https://facebook.com" target="_blank" class="icon bg-primary">
          <i class="fab fa-facebook-f"></i>
        </a>
        <a href="https://linkedin.com" target="_blank" class="icon bg-info">
          <i class="fab fa-linkedin-in"></i>
        </a>
        <a href="https://instagram.com" target="_blank" class="icon bg-danger">
          <i class="fab fa-instagram"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue"
import emailjs from "emailjs-com"

const form = ref({ name: "", email: "", message: "" })
const errors = ref({})
const success = ref(false)

function submitForm() {
  errors.value = {}
  success.value = false

  if (!form.value.name) errors.value.name = "Name is required"
  if (!form.value.email) errors.value.email = "Email is required"
  if (!form.value.message) errors.value.message = "Message is required"

  if (Object.keys(errors.value).length === 0) {
    emailjs
      .send(
        "service_hivabz9",   
        "template_no6wyun",  
        {
          from_name: form.value.name,
          from_email: form.value.email,
          message: form.value.message,
          time: new Date().toLocaleString(), 

        },
        "Id2S0lYcOvqF2zOZD"    
      )
      .then(() => {
        success.value = true
        form.value = { name: "", email: "", message: "" }
      })
      .catch((err) => {
        console.error("Error:", err)
      })
  }
}
</script>


<style scoped>
.contact-page {
  background: #000;
  min-height: 100vh;
}

.contact-home {
  padding-top: 100px;
  padding-bottom: 80px;
}
.section-title {
  font-size: 36px;
  color: #fff;
  position: relative;
}
.section-title::after {
  content: "";
  width: 70px;
  height: 3px;
  background: #01a181;
  display: block;
  margin: 12px auto 0;
  border-radius: 2px;
}

/* INFO CARDS */
.info-card {
  background: #00120f7e;
  padding: 20px;
  border-radius: 18px;
  transition: all 0.3s ease;
  color: #fff;
}
.info-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 0 20px rgba(0, 255, 204, 0.3);
}

/* LINKS INSIDE INFO CARDS */
.info-card a {
  color: #00ffcc;
  text-decoration: none;
  font-weight: 500;
}
.info-card a:hover {
  color: #01a181;
  text-decoration: underline;
}

/* MAP */
.map-container {
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 0 20px rgba(0, 255, 204, 0.3);
}
.map {
  filter: grayscale(100%) invert(92%) contrast(90%);
}

/* FORM CARD */
.form-card {
  background-color: #00120f7e;
  border-radius: 22px;
  transition: all 0.3s ease;
}
.form-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 0 20px rgba(0, 255, 204, 0.3);
}

/* INPUTS */
.input-custom {
  background: #111;
  border: 1px solid #333;
  border-radius: 12px;
  color: #fff;
  padding: 12px;
  transition: all 0.3s ease;
}
.input-custom:focus {
  border-color: #01a181;
  box-shadow: 0 0 10px rgba(0, 255, 204, 0.3);
}

/* SUBMIT BUTTON */
.btn-submit {
  background: linear-gradient(45deg, #00ffcc, #01a181);
  border: none;
  border-radius: 14px;
  color: #000;
  font-weight: bold;
  padding: 12px;
  transition: transform 0.2s ease, box-shadow 0.3s ease;
}
.btn-submit:hover {
  transform: translateY(-3px);
  box-shadow: 0 0 20px rgba(0, 255, 204, 0.6);
}

/* SUCCESS CARD */
.alert-card {
  padding: 18px;
  border-radius: 16px;
  font-weight: 500;
  margin-bottom: 20px;
  text-align: center;
}
.success-card {
  background: #01a181;
  color: #fff;
  box-shadow: 0 0 15px rgba(0, 255, 170, 0.5);
}
.fade-in {
  animation: fadeIn 0.6s ease;
}
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* SOCIAL FOOTER */
.social-footer {
  margin-top: 50px;
  display: flex;
  justify-content: center;
  gap: 20px;
}
.icon {
  width: 45px;
  height: 45px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 18px;
  transition: all 0.4s ease;
  cursor: pointer;
}
.icon:hover {
  transform: scale(1.2) rotate(10deg);
  box-shadow: 0 0 15px rgba(0, 255, 204, 0.6);
}
</style>
