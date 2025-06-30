<template>
  <div>
    <!-- Top Bar -->
    <div class="top-bar">
      <div class="container">
        <div class="top-bar-content">
          <div class="contact-info">
            <span><i class="fas fa-phone-alt"></i> 1900 1234</span>
            <span><i class="fas fa-envelope"></i> info@thuctap.com</span>
            <span><i class="fas fa-map-marker-alt"></i> Cần Ther</span>
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

          <button class="mobile-menu-btn" id="mobileMenuBtn">
            <i class="fas fa-bars"></i>
          </button>

          <nav class="main-nav" id="mainNav">
            <button class="close-menu-btn" id="closeMenuBtn">
              <i class=""></i>
            </button>

            <ul class="nav-links">
              <li class="active"><a href="#">Trang chủ</a></li>
              <li>
                <a href="#">Giới thiệu <i class="fas fa-angle-down"></i></a>
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
});

onBeforeUnmount(() => {
  document.removeEventListener("click", handleClickOutside);
});
</script>
