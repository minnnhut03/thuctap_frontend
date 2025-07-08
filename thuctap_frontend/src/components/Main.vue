<template>
  <main class="health-main">
    <section class="health-hero">
      <div class="container">
        <div class="health-hero-content">
          <h1 class="health-hero-title">
            Giải pháp y tế thông minh cho cuộc sống hiện đại
          </h1>
          <p class="health-hero-description">
            Bệnh viện mang đến hệ thống dịch vụ y tế chất lượng cao với công nghệ tiên
            tiến và đội ngũ chuyên gia hàng đầu
          </p>

          <div class="health-hero-buttons">
            <a href="#" class="btn health-hero-button-primary btn-book">Đặt lịch khám</a>
            <a href="#" class="btn health-hero-button-secondary btn-book"
              >Tìm hiểu thêm</a
            >
          </div>

          <div class="health-hero-search">
            <form class="health-hero-search-form">
              <input
                type="text"
                class="health-hero-search-input"
                placeholder="Tìm kiếm dịch vụ, bác sĩ, chuyên khoa..."
              />
              <button type="submit" class="health-hero-search-button btn-book">
                <i class="fas fa-search"></i> Tìm kiếm
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <section class="health-services health-padding">
      <div class="container">
        <div class="text-center">
          <h2 class="health-section-title">Dịch Vụ Nổi Bật</h2>
          <p class="health-section-description">
            Chúng tôi cung cấp các giải pháp y tế toàn diện với chất lượng dịch vụ tốt
            nhất
          </p>
        </div>
        <div class="container health-padding health-services">
          <div class="row g-4 health-services-grid">
            <div class="col-md-4">
              <div class="health-service-card">
                <div class="health-service-image">
                  <img
                    src="https://medpro.vn/wp-content/uploads/2021/12/kham-chuyen-khoa.png"
                    alt="Khám chuyên khoa"
                  />
                </div>
                <div class="health-service-content">
                  <h3 class="health-service-title">Khám Chuyên Khoa</h3>
                  <p class="health-service-description">
                    Khám và điều trị với các bác sĩ chuyên khoa đầu ngành, trang thiết bị
                    hiện đại theo tiêu chuẩn quốc tế.
                  </p>
                  <div
                    class="health-service-meta d-flex justify-content-between align-items-center"
                  >
                    <a href="#" class="btn btn-book health-service-btn">Đặt lịch</a>
                    <span class="health-service-phone"
                      ><i class="bi bi-telephone-fill"></i> 1900 1234</span
                    >
                  </div>
                </div>
              </div>
            </div>

            <div class="col-md-4">
              <div class="health-service-card">
                <div class="health-service-image">
                  <img
                    src="https://medpro.vn/wp-content/uploads/2021/12/kham-chuyen-khoa.png"
                    alt="Khám chuyên khoa"
                  />
                </div>
                <div class="health-service-content">
                  <h3 class="health-service-title">Khám Chuyên Khoa</h3>
                  <p class="health-service-description">
                    Khám và điều trị với các bác sĩ chuyên khoa đầu ngành, trang thiết bị
                    hiện đại theo tiêu chuẩn quốc tế.
                  </p>
                  <div
                    class="health-service-meta d-flex justify-content-between align-items-center"
                  >
                    <a href="#" class="btn btn-book health-service-btn">Đặt lịch</a>
                    <span class="health-service-phone"
                      ><i class="bi bi-telephone-fill"></i> 1900 1234</span
                    >
                  </div>
                </div>
              </div>
            </div>

            <div class="col-md-4">
              <div class="health-service-card">
                <div class="health-service-image">
                  <img
                    src="https://medpro.vn/wp-content/uploads/2021/12/kham-chuyen-khoa.png"
                    alt="Khám chuyên khoa"
                  />
                </div>
                <div class="health-service-content">
                  <h3 class="health-service-title">Khám Chuyên Khoa</h3>
                  <p class="health-service-description">
                    Khám và điều trị với các bác sĩ chuyên khoa đầu ngành, trang thiết bị
                    hiện đại theo tiêu chuẩn quốc tế.
                  </p>
                  <div
                    class="health-service-meta d-flex justify-content-between align-items-center"
                  >
                    <a href="#" class="btn btn-book health-service-btn">Đặt lịch</a>
                    <span class="health-service-phone"
                      ><i class="bi bi-telephone-fill"></i> 1900 1234</span
                    >
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="health-about health-padding bg-white">
      <div class="container">
        <div class="row align-items-center gy-4">
          <div class="col-lg-6 order-1 order-lg-2">
            <div class="health-about-image">
              <img
                src="https://medpro.vn/wp-content/uploads/2021/12/about-medpro.jpg"
                alt="Giới thiệu MedPro"
                class="img-fluid rounded shadow"
              />
            </div>
          </div>
          <div class="col-lg-6 order-2 order-lg-1">
            <div class="health-about-text">
              <h2 class="mb-3">MedPro - Hệ Thống Y Tế Thông Minh</h2>
              <p>
                Với hơn 10 năm kinh nghiệm trong lĩnh vực chăm sóc sức khỏe, MedPro tự hào
                là đơn vị tiên phong trong ứng dụng công nghệ vào lĩnh vực y tế tại Việt
                Nam.
              </p>

              <ul class="list-unstyled mt-4">
                <li class="d-flex mb-3">
                  <i class="bi bi-check-circle-fill text-success-custom fs-5 me-3"></i>
                  <div>
                    <h5 class="mb-1">Đội ngũ chuyên gia</h5>
                    <p class="mb-0">Hơn 200 bác sĩ chuyên khoa giỏi, nhiều kinh nghiệm</p>
                  </div>
                </li>
                <li class="d-flex mb-3">
                  <i class="bi bi-check-circle-fill text-success-custom fs-5 me-3"></i>
                  <div>
                    <h5 class="mb-1">Công nghệ tiên tiến</h5>
                    <p class="mb-0">Hệ thống máy móc hiện đại đạt chuẩn quốc tế</p>
                  </div>
                </li>
                <li class="d-flex">
                  <i class="bi bi-check-circle-fill text-success-custom fs-5 me-3"></i>
                  <div>
                    <h5 class="mb-1">Dịch vụ toàn diện</h5>
                    <p class="mb-0">
                      Đa dạng dịch vụ từ khám chữa bệnh đến chăm sóc sức khỏe
                    </p>
                  </div>
                </li>
              </ul>

              <a href="#" class="btn btn-book mt-4">Tìm hiểu thêm</a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="health-doctors health-padding">
      <div class="container">
        <div class="text-center">
          <h2 class="health-section-title">Đội Ngũ Bác Sĩ</h2>
          <p class="health-section-description">
            Đội ngũ chuyên gia đầu ngành với nhiều năm kinh nghiệm
          </p>
        </div>
        <div class="container health-doctors health-padding">
          <div class="row g-4 health-doctors-grid">
            <div class="col-md-4">
              <div class="health-doctor-card">
                <div class="health-doctor-img">
                  <img
                    src="https://medpro.vn/wp-content/uploads/2021/12/doctor-1.jpg"
                    alt="Bác sĩ Nguyễn Văn A"
                    class="img-fluid rounded"
                  />
                </div>
                <div class="health-doctor-info mt-3">
                  <h3 class="h5 mb-1">TS. BS Nguyễn Văn A</h3>
                  <span class="text-muted small d-block mb-2">Chuyên khoa Tim mạch</span>
                  <p>
                    Với hơn 20 năm kinh nghiệm trong lĩnh vực tim mạch, từng tu nghiệp tại
                    Mỹ và Pháp.
                  </p>
                  <div class="health-doctor-social d-flex gap-3 mt-2">
                    <a href="#"><i class="bi bi-facebook"></i></a>
                    <a href="#"><i class="bi bi-twitter"></i></a>
                    <a href="#"><i class="bi bi-linkedin"></i></a>
                  </div>
                </div>
              </div>
            </div>
            <div class="col-md-4">
              <div class="health-doctor-card">
                <div class="health-doctor-img">
                  <img
                    src="https://medpro.vn/wp-content/uploads/2021/12/doctor-1.jpg"
                    alt="Bác sĩ Nguyễn Văn A"
                    class="img-fluid rounded"
                  />
                </div>
                <div class="health-doctor-info mt-3">
                  <h3 class="h5 mb-1">TS. BS Nguyễn Văn A</h3>
                  <span class="text-muted small d-block mb-2">Chuyên khoa Tim mạch</span>
                  <p>
                    Với hơn 20 năm kinh nghiệm trong lĩnh vực tim mạch, từng tu nghiệp tại
                    Mỹ và Pháp.
                  </p>
                  <div class="health-doctor-social d-flex gap-3 mt-2">
                    <a href="#"><i class="bi bi-facebook"></i></a>
                    <a href="#"><i class="bi bi-twitter"></i></a>
                    <a href="#"><i class="bi bi-linkedin"></i></a>
                  </div>
                </div>
              </div>
            </div>
            <!-- Repeat for other doctors -->
          </div>

          <div class="text-center mt-5">
            <a href="#" class="btn btn-book">Xem tất cả bác sĩ</a>
          </div>
        </div>
      </div>
    </section>

    <section class="health-cta health-padding">
      <div class="container text-center">
        <h2 class="health-cta-title">Bạn cần tư vấn từ chuyên gia?</h2>
        <p class="health-cta-description">
          Đội ngũ tư vấn viên của chúng tôi luôn sẵn sàng hỗ trợ bạn 24/7
        </p>
        <a href="#" class="btn health-hero-button-secondary btn-book">Liên hệ ngay</a>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section class="health-testimonials health-padding bg-light">
      <div class="container">
        <div class="section-title text-center">
          <h2>Khách Hàng Nói Về Chúng Tôi</h2>
          <p>Những phản hồi từ khách hàng đã sử dụng dịch vụ của MedPro</p>
        </div>

        <div class="health-testimonials-slider">
          <!-- Testimonial Item 1 -->
          <div class="health-testimonial-card">
            <div class="health-testimonial-text">
              "Tôi rất hài lòng với dịch vụ của MedPro. Bác sĩ rất tận tâm, cơ sở vật chất
              hiện đại. Đặc biệt là dịch vụ đặt lịch online rất tiện lợi, tiết kiệm thời
              gian."
            </div>
            <div class="health-testimonial-author">
              <div class="health-author-img">
                <img
                  src="https://randomuser.me/api/portraits/women/65.jpg"
                  alt="Nguyễn Thị Mai"
                />
              </div>
              <div class="health-author-info">
                <h4>Nguyễn Thị Mai</h4>
                <p>Khách hàng thân thiết</p>
              </div>
            </div>
          </div>

          <!-- Testimonial Item 2 -->
          <div class="health-testimonial-card">
            <div class="health-testimonial-text">
              "Dịch vụ khám từ xa của MedPro rất tuyệt vời. Tôi ở tỉnh xa nhưng vẫn được
              bác sĩ giỏi ở Hà Nội tư vấn. Kết quả điều trị rất tốt, tôi sẽ tiếp tục sử
              dụng dịch vụ này."
            </div>
            <div class="health-testimonial-author">
              <div class="health-author-img">
                <img
                  src="https://randomuser.me/api/portraits/men/32.jpg"
                  alt="Trần Văn Nam"
                />
              </div>
              <div class="health-author-info">
                <h4>Trần Văn Nam</h4>
                <p>Khách hàng tại Đà Nẵng</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>
