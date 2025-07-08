<template>
  <div>
    <!-- Top Bar -->
    <div class="top-bar">
      <div class="container">
        <div class="top-bar-content">
          <div class="contact-info">
            <span><i class="fas fa-phone-alt"></i> 1900 1234</span>
            <span><i class="fas fa-envelope"></i> info@thuctap.com</span>
            <span><i class="fas fa-map-marker-alt"></i> Cần Thơ</span>
          </div>
          <div class="social-links">
            <a href="#"><i class="fab fa-facebook-f"></i></a>
            <a href="#"><i class="fab fa-twitter"></i></a>
            <a href="#"><i class="fab fa-linkedin-in"></i></a>
            <a href="#"><i class="fab fa-youtube"></i></a>
          </div>
        </div>
      </div>
    </div>

    <!-- Main Header -->
    <header class="main-header">
      <div class="container">
        <div class="header-content">
          <a href="index.html" class="logo">
            <img
              src="https://tse4.mm.bing.net/th?id=OIP.sd607I1-Pyr_aROuAyw1RgHaHk&pid=Api&P=0&h=180"
              alt="MedPro Logo"
            />
          </a>

          <button class="mobile-menu-btn" id="mobileMenuBtn" @click="toggleMenu">
            <i class="fas fa-bars"></i>
          </button>

          <nav class="main-nav" :class="{ 'nav-open': isMenuOpen }" ref="mainNav" id="mainNav">
            <button class="close-menu-btn" id="closeMenuBtn" @click="toggleMenu">
              <i class="fas fa-times"></i>
            </button>

            <ul class="nav-links">
              <li class="active"><a href="#">Trang chủ</a></li>
              <li>
                <a href="#" @click="toggleDropdown">Giới thiệu <i class="fas fa-angle-down"></i></a>
                <ul class="dropdown-menu">
                  <li><a href="#">Về VCL</a></li>
                  <li><a href="#">Đội ngũ bác sĩ</a></li>
                  <li><a href="#">Cơ sở vật chất</a></li>
                  <li><a href="#">Giải thưởng</a></li>
                </ul>
              </li>
              <li><a href="#">Dịch vụ</a></li>
              <li><a href="#">Bác sĩ</a></li>
              <li><a href="#">Tin tức</a></li>
              <li><a href="#">Liên hệ</a></li>
            </ul>

            <a href="#" class="btn btn-primary">Đặt lịch ngay</a>
          </nav>
        </div>
      </div>
    </header>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const isMenuOpen = ref(false);
const mainNav = ref(null);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const isMobile = () => window.innerWidth <= 992;

const toggleDropdown = (event) => {
  if (isMobile()) {
    event.preventDefault();
    event.currentTarget.classList.toggle("active");
  }
};

const handleClickOutside = (event) => {
  if (
    mainNav.value &&
    !mainNav.value.contains(event.target) &&
    !event.target.closest(".mobile-menu-btn")
  ) {
    isMenuOpen.value = false;
  }
};

onMounted(() => {
  document.addEventListener("click", handleClickOutside);
  
  // Add Font Awesome if not already included
  if (!document.querySelector('link[href*="font-awesome"]')) {
    const link = document.createElement('link');
    link.rel = 'stylesheet';
    link.href = 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css';
    document.head.appendChild(link);
  }
});

onBeforeUnmount(() => {
  document.removeEventListener("click", handleClickOutside);
});
</script>

<style scoped>
/* Top Bar Styles */
.top-bar {
  background: #22d3ee;
  color: white;
  padding: 8px 0;
  font-size: 14px;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1001;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.top-bar-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.contact-info {
  display: flex;
  gap: 30px;
}

.contact-info span {
  display: flex;
  align-items: center;
  gap: 8px;
}

.social-links {
  display: flex;
  gap: 15px;
}

.social-links a {
  color: white;
  font-size: 16px;
  transition: opacity 0.3s;
}

.social-links a:hover {
  opacity: 0.8;
}

/* Main Header Styles */
.main-header {
  background: white;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  position: fixed;
  top: 40px; /* Height of top bar */
  left: 0;
  right: 0;
  z-index: 1000;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 0;
}

.logo img {
  height: 50px;
  width: auto;
}

.mobile-menu-btn {
  display: none;
  background: none;
  border: none;
  font-size: 24px;
  color: #333;
  cursor: pointer;
}

.main-nav {
  display: flex;
  align-items: center;
  gap: 30px;
}

.close-menu-btn {
  display: none;
  background: none;
  border: none;
  font-size: 24px;
  color: #333;
  cursor: pointer;
  position: absolute;
  top: 20px;
  right: 20px;
}

.nav-links {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 30px;
}

.nav-links li {
  position: relative;
}

.nav-links a {
  color: #333;
  text-decoration: none;
  font-weight: 500;
  padding: 10px 0;
  display: flex;
  align-items: center;
  gap: 5px;
  transition: color 0.3s;
}

.nav-links li.active a,
.nav-links a:hover {
  color: #22d3ee;
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  background: white;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  padding: 10px 0;
  min-width: 200px;
  opacity: 0;
  visibility: hidden;
  transform: translateY(-10px);
  transition: all 0.3s;
  list-style: none;
  margin: 0;
}

.nav-links li:hover .dropdown-menu {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
}

.dropdown-menu li {
  padding: 0;
}

.dropdown-menu a {
  padding: 10px 20px;
  color: #666;
  border-bottom: none;
}

.dropdown-menu a:hover {
  background: #f8f9fa;
  color: #22d3ee;
}

.btn {
  padding: 12px 25px;
  border-radius: 25px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s;
  border: none;
  cursor: pointer;
}

.btn-primary {
  background: #3b82f6;
  color: white;
}

.btn-primary:hover {
  background: #2563eb;
  transform: translateY(-2px);
}

/* Mobile Styles */
@media (max-width: 992px) {
  .top-bar {
    display: none;
  }
  
  .main-header {
    top: 0;
  }
  
  .mobile-menu-btn {
    display: block;
  }
  
  .main-nav {
    position: fixed;
    top: 0;
    right: -100%;
    width: 300px;
    height: 100vh;
    background: white;
    flex-direction: column;
    align-items: flex-start;
    padding: 80px 30px 30px;
    transition: right 0.3s;
    box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
  }
  
  .main-nav.nav-open {
    right: 0;
  }
  
  .close-menu-btn {
    display: block;
  }
  
  .nav-links {
    flex-direction: column;
    width: 100%;
    gap: 0;
  }
  
  .nav-links li {
    width: 100%;
    border-bottom: 1px solid #eee;
  }
  
  .nav-links a {
    padding: 15px 0;
    width: 100%;
  }
  
  .dropdown-menu {
    position: static;
    box-shadow: none;
    background: #f8f9fa;
    margin-left: 20px;
    border-radius: 0;
    opacity: 1;
    visibility: visible;
    transform: none;
    display: none;
  }
  
  .nav-links li.active .dropdown-menu {
    display: block;
  }
  
  .btn {
    margin-top: 20px;
    text-align: center;
    display: block;
  }
}

@media (max-width: 768px) {
  .contact-info {
    gap: 15px;
    font-size: 12px;
  }
  
  .contact-info span:last-child {
    display: none;
  }
  
  .social-links {
    gap: 10px;
  }
  
  .main-nav {
    width: 280px;
  }
}
</style>