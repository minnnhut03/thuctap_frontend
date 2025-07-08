<template>
  <div>
    <div class="health-topbar py-3 d-none d-lg-block">
      <div class="container d-flex justify-content-between align-items-center">
        <div class="health-contact-info d-flex gap-4">
          <span><i class="bi bi-telephone-fill"></i> 1900 1234</span>
          <span><i class="bi bi-envelope-fill"></i> info@thuctap.com</span>
          <span><i class="bi bi-geo-alt-fill"></i> Cần Thơ</span>
        </div>
        <div class="health-social-links d-flex gap-3">
          <a href="#"><i class="bi bi-facebook"></i></a>
          <a href="#"><i class="bi bi-twitter-x"></i></a>
          <a href="#"><i class="bi bi-linkedin"></i></a>
          <a href="#"><i class="bi bi-youtube"></i></a>
        </div>
      </div>
    </div>

    <header class="health-header py-3">
      <div class="container d-flex flex-wrap justify-content-between align-items-center">
        <a href="index.html" class="health-logo">
          <img
            src="https://tse4.mm.bing.net/th?id=OIP.sd607I1-Pyr_aROuAyw1RgHaHk&pid=Api&P=0&h=180"
            alt="MedPro Logo"
          />
        </a>

        <nav class="health-nav d-none d-lg-flex align-items-center gap-4">
          <ul class="nav health-nav-links align-items-center mb-0">
            <li class="nav-item"><a class="nav-link active" href="#">Trang chủ</a></li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="aboutDropdown"
                data-bs-toggle="dropdown"
                >Giới thiệu</a
              >
              <ul class="dropdown-menu">
                <li><a class="dropdown-item" href="#">Về VCL</a></li>
                <li><a class="dropdown-item" href="#">Đội ngũ bác sĩ</a></li>
                <li><a class="dropdown-item" href="#">Cơ sở vật chất</a></li>
                <li><a class="dropdown-item" href="#">Giải thưởng</a></li>
              </ul>
            </li>
            <li class="nav-item"><a class="nav-link" href="#">Dịch vụ</a></li>
            <li class="nav-item"><a class="nav-link" href="#">Bác sĩ</a></li>
            <li class="nav-item"><a class="nav-link" href="#">Tin tức</a></li>
            <li class="nav-item"><a class="nav-link" href="#">Liên hệ</a></li>
          </ul>
          <a href="#" class="btn btn-book px-4">Đặt lịch ngay</a>
        </nav>

        <!-- Mobile Menu Button -->
        <button
          class="btn d-lg-none text-primary fs-3"
          type="button"
          data-bs-toggle="offcanvas"
          data-bs-target="#mobileMenu"
        >
          <i class="bi bi-list"></i>
        </button>

        <!-- Offcanvas Sidebar for Mobile -->
        <div class="offcanvas offcanvas-end" tabindex="-1" id="mobileMenu">
          <div class="offcanvas-header">
            <h5 class="offcanvas-title">Menu</h5>
            <button type="button" class="btn-close" data-bs-dismiss="offcanvas"></button>
          </div>
          <div class="offcanvas-body d-flex flex-column">
            <ul class="nav flex-column flex-grow-1">
              <li class="nav-item"><a class="nav-link" href="#">Trang chủ</a></li>
              <li class="nav-item dropdown">
                <a
                  class="nav-link dropdown-toggle"
                  href="#"
                  id="mobileAbout"
                  data-bs-toggle="collapse"
                  data-bs-target="#aboutCollapse"
                  >Giới thiệu</a
                >
                <div class="collapse" id="aboutCollapse">
                  <ul class="list-unstyled ps-3">
                    <li><a class="nav-link" href="#">Về VCL</a></li>
                    <li><a class="nav-link" href="#">Đội ngũ bác sĩ</a></li>
                    <li><a class="nav-link" href="#">Cơ sở vật chất</a></li>
                    <li><a class="nav-link" href="#">Giải thưởng</a></li>
                  </ul>
                </div>
              </li>
              <li class="nav-item"><a class="nav-link" href="#">Dịch vụ</a></li>
              <li class="nav-item"><a class="nav-link" href="#">Bác sĩ</a></li>
              <li class="nav-item"><a class="nav-link" href="#">Tin tức</a></li>
              <li class="nav-item"><a class="nav-link" href="#">Liên hệ</a></li>
            </ul>
            <a href="#" class="btn btn-book w-100 mt-auto">Đặt lịch ngay</a>
          </div>
        </div>
      </div>
    </header>
  </div>
</template>

<script setup>
import { onMounted, onBeforeUnmount } from "vue";

const handleResize = () => {
  if (window.innerWidth >= 992) {
    const offcanvasEl = document.getElementById("mobileMenu");
    const bsOffcanvas = bootstrap.Offcanvas.getInstance(offcanvasEl);
    if (bsOffcanvas) {
      bsOffcanvas.hide();
    }

    // Đóng tất cả collapse đang mở trong offcanvas
    const openCollapses = document.querySelectorAll(".offcanvas .collapse.show");
    openCollapses.forEach((collapseEl) => {
      const bsCollapse =
        bootstrap.Collapse.getInstance(collapseEl) ||
        new bootstrap.Collapse(collapseEl, { toggle: false });
      bsCollapse.hide();
    });
  }
};

onMounted(() => {
  window.addEventListener("resize", handleResize);
});

onBeforeUnmount(() => {
  window.removeEventListener("resize", handleResize);
});
</script>
