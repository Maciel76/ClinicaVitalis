<template>
  <div class="vitalis-clinic">
    <!-- Preloader Premium -->
    <div v-if="loading" class="preloader">
      <div class="preloader-logo">
        <svg viewBox="0 0 200 60" class="vitalis-logo">
          <path
            class="logo-path"
            d="M20,30 Q30,10 40,30 Q50,50 60,30 Q70,10 80,30"
            stroke="#9C7A6B"
            fill="none"
            stroke-width="3"
          />
          <text x="100" y="50" class="logo-text">VITALIS</text>
        </svg>
      </div>
      <div class="preloader-progress"></div>
    </div>

    <!-- Cabeçalho Luxuoso -->
    <header class="header" :class="{ scrolled: isScrolled }">
      <div class="container">
        <div class="header-inner">
          <router-link to="/" class="logo">
            <svg viewBox="0 0 200 60" class="vitalis-logo">
              <path
                class="logo-path"
                d="M20,30 Q30,10 40,30 Q50,50 60,30 Q70,10 80,30"
                stroke="#9C7A6B"
                fill="none"
                stroke-width="3"
              />
              <text x="100" y="40" class="logo-text">VITALIS</text>
            </svg>
          </router-link>

          <nav class="main-nav">
            <ul>
              <li><a href="#home" class="nav-link active">Início</a></li>
              <li><a href="#services" class="nav-link">Serviços</a></li>
              <li><a href="#about" class="nav-link">Sobre</a></li>
              <li><a href="#gallery" class="nav-link">Galeria</a></li>
              <li><a href="#testimonials" class="nav-link">Depoimentos</a></li>
              <li><a href="#contact" class="nav-link">Contato</a></li>
            </ul>
          </nav>

          <div class="header-actions">
            <button class="btn-cta" @click="openModal('booking')">
              Agendar Consulta
            </button>
            <button class="menu-toggle" @click="toggleMobileMenu">
              <span></span>
              <span></span>
              <span></span>
            </button>
          </div>
        </div>
      </div>
    </header>

    <!-- Menu Mobile -->
    <div class="mobile-menu" :class="{ active: mobileMenuOpen }">
      <div class="mobile-menu-inner">
        <nav>
          <ul>
            <li>
              <a href="#home" class="nav-link" @click="closeMobileMenu"
                >Início</a
              >
            </li>
            <li>
              <a href="#services" class="nav-link" @click="closeMobileMenu"
                >Serviços</a
              >
            </li>
            <li>
              <a href="#about" class="nav-link" @click="closeMobileMenu"
                >Sobre</a
              >
            </li>
            <li>
              <a href="#gallery" class="nav-link" @click="closeMobileMenu"
                >Galeria</a
              >
            </li>
            <li>
              <a href="#testimonials" class="nav-link" @click="closeMobileMenu"
                >Depoimentos</a
              >
            </li>
            <li>
              <a href="#contact" class="nav-link" @click="closeMobileMenu"
                >Contato</a
              >
            </li>
          </ul>
        </nav>
        <button class="btn-cta" @click="openModal('booking')">
          Agendar Consulta
        </button>
      </div>
    </div>

    <!-- Hero Section -->
    <section id="home" class="hero">
      <div class="hero-slider">
        <div
          class="slide active"
          style="
            background-image: url('https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?ixlib=rb-1.2.1&auto=format&fit=crop&w=1950&q=80');
          "
        >
          <div class="container">
            <div class="hero-content">
              <h1 class="hero-title">
                Beleza que <span>renova</span> sua essência
              </h1>
              <p class="hero-subtitle">
                Tratamentos premium para realçar sua beleza natural
              </p>
              <div class="hero-actions">
                <button class="btn-cta" @click="openModal('booking')">
                  Agendar Consulta
                </button>
                <button
                  class="btn-outline"
                  @click="scrollToSection('services')"
                >
                  Nossos Serviços
                </button>
              </div>
            </div>
          </div>
        </div>
        <div
          class="slide"
          style="
            background-image: url('https://plus.unsplash.com/premium_photo-1675686363460-25aa1039e94b?q=80&w=2043&auto=format&fit=crop');
          "
        >
          <div class="container">
            <div class="hero-content">
              <h1 class="hero-title">
                Experiência de <span>luxo</span> e bem-estar
              </h1>
              <p class="hero-subtitle">
                Tecnologia avançada com atendimento personalizado
              </p>
              <div class="hero-actions">
                <button class="btn-cta" @click="openModal('booking')">
                  Agendar Consulta
                </button>
                <button
                  class="btn-outline"
                  @click="scrollToSection('services')"
                >
                  Nossos Serviços
                </button>
              </div>
            </div>
          </div>
        </div>
        <div
          class="slide"
          style="
            background-image: url('https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?ixlib=rb-1.2.1&auto=format&fit=crop&w=1950&q=80');
          "
        >
          <div class="container">
            <div class="hero-content">
              <h1 class="hero-title">
                Sua jornada para a <span>confiança</span>
              </h1>
              <p class="hero-subtitle">
                Resultados visíveis desde a primeira sessão
              </p>
              <div class="hero-actions">
                <button class="btn-cta" @click="openModal('booking')">
                  Agendar Consulta
                </button>
                <button
                  class="btn-outline"
                  @click="scrollToSection('services')"
                >
                  Nossos Serviços
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="hero-slider-controls">
        <button class="slider-prev" @click="prevSlide">‹</button>
        <div class="slider-dots">
          <span
            v-for="(slide, index) in 3"
            :key="index"
            :class="{ active: currentSlide === index }"
            @click="goToSlide(index)"
          ></span>
        </div>
        <button class="slider-next" @click="nextSlide">›</button>
      </div>
      <div class="scroll-down" @click="scrollToSection('services')">
        <span></span>
      </div>
    </section>

    <!-- Serviços Premium -->
    <section id="services" class="services-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">Nossos <span>Serviços</span> Exclusivos</h2>
          <p class="section-subtitle">
            Tratamentos personalizados com tecnologia de ponta
          </p>
          <div class="divider"></div>
        </div>

        <div class="services-grid">
          <div
            class="service-card"
            v-for="(service, index) in services"
            :key="index"
          >
            <div class="service-icon">
              <img :src="service.icon" :alt="service.title" />
            </div>
            <h3 class="service-title">{{ service.title }}</h3>
            <p class="service-description">{{ service.description }}</p>
            <button class="btn-service" @click="openServiceModal(service)">
              Saiba mais
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Sobre a Clínica -->
    <section id="about" class="about-section">
      <div class="container">
        <div class="about-content">
          <div class="about-image">
            <img
              src="https://images.unsplash.com/photo-1579684385127-1ef15d508118?ixlib=rb-1.2.1&auto=format&fit=crop&w=1950&q=80"
              alt="Clínica Vitalis"
            />
          </div>
          <div class="about-text">
            <h2 class="section-title">Sobre a <span>Vitalis</span></h2>
            <p>
              A Vitalis é um espaço de excelência em estética e bem-estar, onde
              combinamos tecnologia avançada com atendimento personalizado para
              oferecer resultados excepcionais.
            </p>

            <div class="about-features">
              <div class="feature">
                <div class="feature-icon">
                  <i class="icon-star"></i>
                </div>
                <div class="feature-text">
                  <h4>Profissionais Certificados</h4>
                  <p>Equipe especializada com formação internacional</p>
                </div>
              </div>
              <div class="feature">
                <div class="feature-icon">
                  <i class="icon-award"></i>
                </div>
                <div class="feature-text">
                  <h4>Tecnologia de Ponta</h4>
                  <p>Equipamentos premium para resultados superiores</p>
                </div>
              </div>
              <div class="feature">
                <div class="feature-icon">
                  <i class="icon-heart"></i>
                </div>
                <div class="feature-text">
                  <h4>Ambiente Exclusivo</h4>
                  <p>Design que promove conforto e privacidade</p>
                </div>
              </div>
            </div>

            <button class="btn-cta" @click="openModal('about')">
              Conheça nossa história
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Galeria -->
    <section id="gallery" class="gallery-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">Nossa <span>Galeria</span></h2>
          <p class="section-subtitle">Resultados que falam por si</p>
          <div class="divider"></div>
        </div>

        <div class="gallery-grid">
          <div
            class="gallery-item"
            v-for="(image, index) in galleryImages"
            :key="index"
            @click="openGallery(index)"
          >
            <img :src="image.thumb" :alt="'Imagem ' + (index + 1)" />
            <div class="gallery-overlay">
              <i class="icon-zoom"></i>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Depoimentos -->
    <section id="testimonials" class="testimonials-section">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">Depoimentos de <span>Clientes</span></h2>
          <p class="section-subtitle">A satisfação que nos inspira</p>
          <div class="divider"></div>
        </div>

        <div class="testimonials-slider">
          <div
            class="testimonials-track"
            :style="{
              transform: 'translateX(' + -currentTestimonial * 100 + '%)',
            }"
          >
            <div
              class="testimonial"
              v-for="(testimonial, index) in testimonials"
              :key="index"
            >
              <div class="testimonial-content">
                <div class="testimonial-avatar">
                  <img :src="testimonial.avatar" :alt="testimonial.name" />
                </div>
                <div class="testimonial-text">
                  <p>"{{ testimonial.text }}"</p>
                  <div class="testimonial-author">
                    <h4>{{ testimonial.name }}</h4>
                    <span>{{ testimonial.role }}</span>
                  </div>
                  <div class="testimonial-rating">
                    <i
                      v-for="star in 5"
                      :key="star"
                      :class="
                        star <= testimonial.rating
                          ? 'icon-star-filled'
                          : 'icon-star'
                      "
                    ></i>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="testimonials-controls">
            <button class="slider-prev" @click="prevTestimonial">‹</button>
            <div class="slider-dots">
              <span
                v-for="(testimonial, index) in testimonials"
                :key="index"
                :class="{ active: currentTestimonial === index }"
                @click="goToTestimonial(index)"
              ></span>
            </div>
            <button class="slider-next" @click="nextTestimonial">›</button>
          </div>
        </div>
      </div>
    </section>

    <!-- Contato -->
    <section id="contact" class="contact-section">
      <div class="container">
        <div class="contact-content">
          <div class="contact-info">
            <h2 class="section-title">Entre em <span>Contato</span></h2>
            <p>
              Estamos à disposição para esclarecer dúvidas e agendar sua
              avaliação personalizada.
            </p>

            <div class="contact-details">
              <div class="contact-item">
                <i class="icon-location"></i>
                <div>
                  <h4>Endereço</h4>
                  <p>Av. Premium, 1000 - Jardim Luxo<br />São Paulo - SP</p>
                </div>
              </div>
              <div class="contact-item">
                <i class="icon-phone"></i>
                <div>
                  <h4>Telefone</h4>
                  <p>(11) 99999-9999</p>
                </div>
              </div>
              <div class="contact-item">
                <i class="icon-email"></i>
                <div>
                  <h4>Email</h4>
                  <p>contato@vitalisestetica.com.br</p>
                </div>
              </div>
              <div class="contact-item">
                <i class="icon-clock"></i>
                <div>
                  <h4>Horário de Funcionamento</h4>
                  <p>Segunda a Sexta: 9h às 20h<br />Sábado: 9h às 16h</p>
                </div>
              </div>
            </div>

            <div class="social-links">
              <a href="#" class="social-icon"><i class="icon-instagram"></i></a>
              <a href="#" class="social-icon"><i class="icon-facebook"></i></a>
              <a href="#" class="social-icon"><i class="icon-whatsapp"></i></a>
            </div>
          </div>

          <div class="contact-form">
            <form @submit.prevent="submitForm">
              <div class="form-group">
                <input
                  type="text"
                  v-model="form.name"
                  placeholder="Seu nome"
                  required
                />
              </div>
              <div class="form-group">
                <input
                  type="email"
                  v-model="form.email"
                  placeholder="Seu email"
                  required
                />
              </div>
              <div class="form-group">
                <input
                  type="tel"
                  v-model="form.phone"
                  placeholder="Seu telefone"
                />
              </div>
              <div class="form-group">
                <select v-model="form.service" required>
                  <option value="" disabled selected>
                    Selecione um serviço
                  </option>
                  <option
                    v-for="(service, index) in services"
                    :key="index"
                    :value="service.title"
                  >
                    {{ service.title }}
                  </option>
                </select>
              </div>
              <div class="form-group">
                <textarea
                  v-model="form.message"
                  placeholder="Sua mensagem"
                  rows="4"
                ></textarea>
              </div>
              <button type="submit" class="btn-cta">Enviar Mensagem</button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Rodapé Premium -->
    <footer class="footer">
      <div class="container">
        <div class="footer-content">
          <div class="footer-logo">
            <svg viewBox="0 0 200 60" class="vitalis-logo">
              <path
                class="logo-path"
                d="M20,30 Q30,10 40,30 Q50,50 60,30 Q70,10 80,30"
                stroke="#9C7A6B"
                fill="none"
                stroke-width="3"
              />
              <text x="100" y="40" class="logo-text">VITALIS</text>
            </svg>
            <p>Excelência em estética e bem-estar</p>
          </div>

          <div class="footer-links">
            <div class="links-column">
              <h4>Serviços</h4>
              <ul>
                <li
                  v-for="(service, index) in services.slice(0, 4)"
                  :key="index"
                >
                  <a href="#" @click="openServiceModal(service)">{{
                    service.title
                  }}</a>
                </li>
              </ul>
            </div>
            <div class="links-column">
              <h4>Links Rápidos</h4>
              <ul>
                <li><a href="#home">Início</a></li>
                <li><a href="#services">Serviços</a></li>
                <li><a href="#about">Sobre</a></li>
                <li><a href="#gallery">Galeria</a></li>
              </ul>
            </div>
            <div class="links-column">
              <h4>Contato</h4>
              <ul>
                <li><a href="tel:+5511999999999">(11) 99999-9999</a></li>
                <li>
                  <a href="mailto:contato@vitalisestetica.com.br"
                    >contato@vitalisestetica.com.br</a
                  >
                </li>
                <li>Av. Premium, 1000</li>
                <li>São Paulo - SP</li>
              </ul>
            </div>
          </div>
        </div>

        <div class="footer-bottom">
          <p>&copy; 2023 Vitalis Estética. Todos os direitos reservados.</p>
          <div class="footer-legal">
            <a href="#">Política de Privacidade</a>
            <a href="#">Termos de Uso</a>
          </div>
        </div>
      </div>
    </footer>

    <!-- Modais -->
    <div
      class="modal-overlay"
      :class="{ active: activeModal }"
      @click="closeModal"
    >
      <div class="modal-container" @click.stop>
        <!-- Modal de Agendamento -->
        <div class="modal booking-modal" v-if="activeModal === 'booking'">
          <button class="modal-close" @click="closeModal">×</button>
          <h3 class="modal-title">Agende sua Consulta</h3>
          <p class="modal-subtitle">
            Preencha o formulário abaixo e nossa equipe entrará em contato para
            confirmar seu horário.
          </p>

          <form @submit.prevent="submitBooking">
            <div class="form-group">
              <input
                type="text"
                v-model="booking.name"
                placeholder="Seu nome completo"
                required
              />
            </div>
            <div class="form-group">
              <input
                type="email"
                v-model="booking.email"
                placeholder="Seu email"
                required
              />
            </div>
            <div class="form-group">
              <input
                type="tel"
                v-model="booking.phone"
                placeholder="Seu telefone"
                required
              />
            </div>
            <div class="form-group">
              <select v-model="booking.service" required>
                <option value="" disabled selected>Selecione um serviço</option>
                <option
                  v-for="(service, index) in services"
                  :key="index"
                  :value="service.title"
                >
                  {{ service.title }}
                </option>
              </select>
            </div>
            <div class="form-row">
              <div class="form-group">
                <input type="date" v-model="booking.date" required />
              </div>
              <div class="form-group">
                <select v-model="booking.time" required>
                  <option value="" disabled selected>Horário</option>
                  <option
                    v-for="time in availableTimes"
                    :key="time"
                    :value="time"
                  >
                    {{ time }}
                  </option>
                </select>
              </div>
            </div>
            <div class="form-group">
              <textarea
                v-model="booking.notes"
                placeholder="Alguma observação ou preferência?"
              ></textarea>
            </div>
            <button type="submit" class="btn-cta">Confirmar Agendamento</button>
          </form>
        </div>

        <!-- Modal de Serviço -->
        <div
          class="modal service-modal"
          v-if="activeModal === 'service' && selectedService"
        >
          <button class="modal-close" @click="closeModal">×</button>
          <div class="service-modal-content">
            <div class="service-modal-image">
              <img :src="selectedService.image" :alt="selectedService.title" />
            </div>
            <div class="service-modal-text">
              <h3 class="modal-title">{{ selectedService.title }}</h3>
              <div class="service-details">
                <div class="detail">
                  <i class="icon-clock"></i>
                  <span>{{ selectedService.duration }} minutos</span>
                </div>
                <div class="detail">
                  <i class="icon-price"></i>
                  <span>{{ selectedService.price }}</span>
                </div>
              </div>
              <p class="service-description">
                {{ selectedService.longDescription }}
              </p>

              <div class="service-benefits">
                <h4>Benefícios:</h4>
                <ul>
                  <li
                    v-for="(benefit, index) in selectedService.benefits"
                    :key="index"
                  >
                    {{ benefit }}
                  </li>
                </ul>
              </div>

              <button class="btn-cta" @click="openModal('booking')">
                Agendar este serviço
              </button>
            </div>
          </div>
        </div>

        <!-- Modal de Galeria -->
        <div
          class="modal gallery-modal"
          v-if="activeModal === 'gallery' && currentGalleryImage !== null"
        >
          <button class="modal-close" @click="closeModal">×</button>
          <div class="gallery-modal-content">
            <img
              :src="galleryImages[currentGalleryImage].full"
              :alt="'Imagem ' + (currentGalleryImage + 1)"
            />
            <button class="gallery-prev" @click="prevGalleryImage">‹</button>
            <button class="gallery-next" @click="nextGalleryImage">›</button>
          </div>
        </div>
      </div>
    </div>

    <!-- Botão Flutuante WhatsApp -->
    <a
      href="https://wa.me/5511999999999"
      class="whatsapp-float"
      target="_blank"
    >
      <i class="icon-whatsapp"></i>
    </a>
  </div>
</template>

<script>
export default {
  name: "VitalisClinic",
  data() {
    return {
      loading: true,
      isScrolled: false,
      mobileMenuOpen: false,
      currentSlide: 0,
      currentTestimonial: 0,
      activeModal: null,
      currentGalleryImage: null,
      selectedService: null,
      form: {
        name: "",
        email: "",
        phone: "",
        service: "",
        message: "",
      },
      booking: {
        name: "",
        email: "",
        phone: "",
        service: "",
        date: "",
        time: "",
        notes: "",
      },
      services: [
        {
          title: "Lifting Facial Premium",
          description:
            "Rejuvenescimento facial com tecnologia de ultrassom microfocado",
          longDescription:
            "O Lifting Facial Premium utiliza tecnologia de ultrassom microfocado para estimular a produção natural de colágeno, proporcionando um efeito lifting imediato e resultados progressivos ao longo de 3 meses. Tratamento não invasivo com zero downtime.",
          icon: "https://cdn-icons-png.flaticon.com/512/3048/3048127.png",
          image:
            "https://images.unsplash.com/photo-1522337360788-8b13dee7a37e?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          duration: 90,
          price: "R$ 1.200,00",
          benefits: [
            "Redução de até 30% das rugas",
            "Melhora na firmeza da pele",
            "Efeito lifting sem cirurgia",
            "Resultados progressivos por até 6 meses",
          ],
        },
        {
          title: "Corporal Integrado",
          description:
            "Protocolo completo para redução de medidas e modelagem corporal",
          longDescription:
            "Nosso protocolo Corporal Integrado combina diferentes tecnologias como radiofrequência, criolipólise e massagem modeladora para oferecer resultados superiores na redução de medidas e modelagem corporal. Programa personalizado de acordo com suas necessidades específicas.",
          icon: "https://cdn-icons-png.flaticon.com/512/3048/3048107.png",
          image:
            "https://images.unsplash.com/photo-1556228578-8c89e6adf883?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          duration: 120,
          price: "R$ 1.800,00 (pacote 6 sessões)",
          benefits: [
            "Redução de medidas localizada",
            "Melhora na flacidez",
            "Estímulo à circulação",
            "Tratamento personalizado",
          ],
        },
        {
          title: "Harmonização Facial",
          description: "Técnicas avançadas para proporção e equilíbrio facial",
          longDescription:
            "A Harmonização Facial na Vitalis vai além da aplicação de preenchedores. Nossos especialistas realizam um estudo facial completo para propor tratamentos que valorizem suas características únicas, utilizando técnicas avançadas e produtos premium para resultados naturais.",
          icon: "https://cdn-icons-png.flaticon.com/512/3048/3048122.png",
          image:
            "https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          duration: 60,
          price: "A partir de R$ 800,00",
          benefits: [
            "Proporção facial equilibrada",
            "Resultados naturais",
            "Técnicas minimamente invasivas",
            "Procedimento personalizado",
          ],
        },
        {
          title: "Peeling de Diamante",
          description: "Renovação celular com tecnologia de ponta",
          longDescription:
            "O Peeling de Diamante é um tratamento de renovação celular que utiliza pontas de diamante para remover as células mortas da superfície da pele, estimulando a produção de colágeno e melhorando a textura e tonalidade da pele. Ideal para tratamento de acne, manchas e sinais de envelhecimento.",
          icon: "https://api.iconify.design/icon-park:diamonds.svg",
          image:
            "https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          duration: 45,
          price: "R$ 350,00",
          benefits: [
            "Melhora na textura da pele",
            "Redução de poros dilatados",
            "Tratamento de manchas",
            "Pele mais luminosa",
          ],
        },
        {
          title: "Drenagem Linfática Premium",
          description:
            "Técnica manual especializada para resultados superiores",
          longDescription:
            "Nossa Drenagem Linfática Premium é realizada por fisioterapeutas especializados que utilizam técnicas manuais avançadas para estimular o sistema linfático, reduzindo inchaços e promovendo a eliminação de toxinas. Inclui avaliação corporal completa e protocolo personalizado.",
          icon: "https://api.iconify.design/fluent-color:premium-16.svg",
          image:
            "https://images.unsplash.com/photo-1544161515-4ab6ce6db874?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          duration: 50,
          price: "R$ 280,00",
          benefits: [
            "Redução de inchaço",
            "Melhora na circulação",
            "Efeito detox",
            "Relaxamento profundo",
          ],
        },
        {
          title: "Tratamento Capilar VIP",
          description: "Reconstrução intensiva para fios danificados",
          longDescription:
            "O Tratamento Capilar VIP da Vitalis é um protocolo de reconstrução intensiva que combina tecnologias como LEDterapia, microinfusão de ativos e cauterização térmica para recuperar fios danificados por químicas, calor ou fatores ambientais. Resultados visíveis desde a primeira sessão.",
          icon: "https://api.iconify.design/flat-color-icons:vip.svg",
          image:
            "https://images.unsplash.com/photo-1519699047748-de8e457a634e?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
          duration: 90,
          price: "R$ 450,00",
          benefits: [
            "Recuperação da fibra capilar",
            "Redução do volume",
            "Fios mais brilhantes",
            "Hidratação profunda",
          ],
        },
      ],
      testimonials: [
        {
          name: "Ana Carolina Silva",
          role: "Executiva de Marketing",
          text: "Os resultados do Lifting Facial superaram todas as minhas expectativas. Minha pele nunca esteve tão firme e luminosa. A equipe da Vitalis é extremamente profissional e atenciosa.",
          rating: 5,
          avatar: "https://randomuser.me/api/portraits/women/43.jpg",
        },
        {
          name: "Roberta Mendes",
          role: "Empresária",
          text: "Fiz o protocolo Corporal Integrado e perdi 8cm de circunferência abdominal em apenas 6 sessões. A clínica tem um ambiente luxuoso e os equipamentos são de última geração.",
          rating: 5,
          avatar: "https://randomuser.me/api/portraits/women/65.jpg",
        },
        {
          name: "Camila Oliveira",
          role: "Dentista",
          text: "A Harmonização Facial feita na Vitalis foi perfeita! Conseguimos resultados naturais que valorizaram meus traços. Recomendo a todos que buscam procedimentos de excelência.",
          rating: 5,
          avatar: "https://randomuser.me/api/portraits/women/32.jpg",
        },
        {
          name: "Fernanda Costa",
          role: "Advogada",
          text: "O atendimento personalizado e a atenção aos detalhes fazem toda a diferença. Me sinto em casa toda vez que venho para minhas sessões de peeling.",
          rating: 4,
          avatar: "https://randomuser.me/api/portraits/women/76.jpg",
        },
      ],
      galleryImages: [
        {
          thumb:
            "https://plus.unsplash.com/premium_photo-1658527022587-07b3d7cd55f5?q=80&w=2070&auto=format&fit=crop",
          full: "https://plus.unsplash.com/premium_photo-1658527022587-07b3d7cd55f5?q=80&w=2070&auto=format&fit=crop",
        },
        {
          thumb:
            "https://images.unsplash.com/photo-1556228578-8c89e6adf883?ixlib=rb-1.2.1&auto=format&fit=crop&w=300&q=80",
          full: "https://images.unsplash.com/photo-1556228578-8c89e6adf883?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80",
        },
        {
          thumb:
            "https://plus.unsplash.com/premium_photo-1677181731363-d9338f1805c8?w=500&auto=format&fit=crop",
          full: "https://plus.unsplash.com/premium_photo-1677181731363-d9338f1805c8?w=500&auto=format&fit=crop",
        },
        {
          thumb:
            "https://images.unsplash.com/photo-1629909614456-6b1c5c94cecc?q=80&w=2094&auto=format&fit=crop",
          full: "https://images.unsplash.com/photo-1629909614456-6b1c5c94cecc?q=80&w=2094&auto=format&fit=crop",
        },
        {
          thumb:
            "https://images.unsplash.com/photo-1544161515-4ab6ce6db874?ixlib=rb-1.2.1&auto=format&fit=crop&w=300&q=80",
          full: "https://images.unsplash.com/photo-1544161515-4ab6ce6db874?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80",
        },
        {
          thumb:
            "https://images.unsplash.com/photo-1519699047748-de8e457a634e?ixlib=rb-1.2.1&auto=format&fit=crop&w=300&q=80",
          full: "https://images.unsplash.com/photo-1519699047748-de8e457a634e?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80",
        },
      ],
      availableTimes: [
        "09:00",
        "10:30",
        "12:00",
        "14:00",
        "15:30",
        "17:00",
        "18:30",
      ],
    };
  },
  computed: {
    heroSlides() {
      return document.querySelectorAll(".hero-slider .slide");
    },
  },
  mounted() {
    // Simular carregamento
    setTimeout(() => {
      this.loading = false;
    }, 1500);

    // Configurar slider automático
    this.startSlider();

    // Configurar scroll listener
    window.addEventListener("scroll", this.handleScroll);

    // Configurar observador de seções para menu ativo
    this.setupSectionObserver();
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
    clearInterval(this.sliderInterval);
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50;
    },
    startSlider() {
      this.sliderInterval = setInterval(() => {
        this.nextSlide();
      }, 5000);
    },
    nextSlide() {
      clearInterval(this.sliderInterval);
      this.currentSlide = (this.currentSlide + 1) % 3;
      this.updateHeroSlider();
      this.startSlider();
    },
    prevSlide() {
      clearInterval(this.sliderInterval);
      this.currentSlide = (this.currentSlide - 1 + 3) % 3;
      this.updateHeroSlider();
      this.startSlider();
    },
    goToSlide(index) {
      clearInterval(this.sliderInterval);
      this.currentSlide = index;
      this.updateHeroSlider();
      this.startSlider();
    },
    updateHeroSlider() {
      const slides = document.querySelectorAll(".hero-slider .slide");
      slides.forEach((slide, index) => {
        if (index === this.currentSlide) {
          slide.classList.add("active");
        } else {
          slide.classList.remove("active");
        }
      });
    },
    nextTestimonial() {
      this.currentTestimonial =
        (this.currentTestimonial + 1) % this.testimonials.length;
    },
    prevTestimonial() {
      this.currentTestimonial =
        (this.currentTestimonial - 1 + this.testimonials.length) %
        this.testimonials.length;
    },
    goToTestimonial(index) {
      this.currentTestimonial = index;
    },
    toggleMobileMenu() {
      this.mobileMenuOpen = !this.mobileMenuOpen;
    },
    closeMobileMenu() {
      this.mobileMenuOpen = false;
    },
    scrollToSection(sectionId) {
      const element = document.getElementById(sectionId);
      if (element) {
        window.scrollTo({
          top: element.offsetTop - 80,
          behavior: "smooth",
        });
      }
    },
    openModal(modalType) {
      this.activeModal = modalType;
      document.body.style.overflow = "hidden";
    },
    closeModal() {
      this.activeModal = null;
      this.selectedService = null;
      this.currentGalleryImage = null;
      document.body.style.overflow = "";
    },
    openServiceModal(service) {
      this.selectedService = service;
      this.openModal("service");
    },
    openGallery(index) {
      this.currentGalleryImage = index;
      this.openModal("gallery");
    },
    nextGalleryImage() {
      this.currentGalleryImage =
        (this.currentGalleryImage + 1) % this.galleryImages.length;
    },
    prevGalleryImage() {
      this.currentGalleryImage =
        (this.currentGalleryImage - 1 + this.galleryImages.length) %
        this.galleryImages.length;
    },
    submitForm() {
      // Simular envio do formulário
      console.log("Formulário enviado:", this.form);
      alert("Mensagem enviada com sucesso! Entraremos em contato em breve.");
      this.form = {
        name: "",
        email: "",
        phone: "",
        service: "",
        message: "",
      };
    },
    submitBooking() {
      // Simular agendamento
      console.log("Agendamento enviado:", this.booking);
      alert(
        "Agendamento solicitado com sucesso! Nossa equipe entrará em contato para confirmação."
      );
      this.booking = {
        name: "",
        email: "",
        phone: "",
        service: "",
        date: "",
        time: "",
        notes: "",
      };
      this.closeModal();
    },
    setupSectionObserver() {
      const sections = document.querySelectorAll("section");
      const navLinks = document.querySelectorAll(".nav-link");

      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              const id = entry.target.getAttribute("id");
              navLinks.forEach((link) => {
                link.classList.remove("active");
                if (link.getAttribute("href") === `#${id}`) {
                  link.classList.add("active");
                }
              });
            }
          });
        },
        { threshold: 0.5 }
      );

      sections.forEach((section) => {
        observer.observe(section);
      });
    },
  },
};
</script>

<style scoped>
/* Estilos premium para a clínica Vitalis */
.vitalis-clinic {
  font-family: "Montserrat", sans-serif;
  color: #333;
  overflow-x: hidden;
}

/* Preloader */
.preloader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #f9f5f2;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.preloader-logo {
  width: 200px;
  margin-bottom: 30px;
}

.preloader-progress {
  height: 2px;
  width: 200px;
  background: #e8d8d0;
  position: relative;
  overflow: hidden;
}

.preloader-progress::after {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 50%;
  background: #9c7a6b;
  animation: loading 1.5s infinite ease-in-out;
}

@keyframes loading {
  0% {
    left: -50%;
  }
  100% {
    left: 150%;
  }
}

/* Logo */
.vitalis-logo {
  width: 200px;
  height: auto;
}

.logo-path {
  stroke-dasharray: 150;
  stroke-dashoffset: 150;
  animation: draw 1.5s ease-in-out forwards;
}

.logo-text {
  font-family: "Playfair Display", serif;
  font-size: 20px;
  fill: #9c7a6b;
  font-weight: 700;
  letter-spacing: 2px;
}

@keyframes draw {
  to {
    stroke-dashoffset: 0;
  }
}

/* Header */
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 20px 0;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  z-index: 1000;
  transition: all 0.3s ease;
}

.header.scrolled {
  padding: 15px 0;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
}

.header-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.main-nav ul {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

.main-nav li {
  margin: 0 15px;
}

.nav-link {
  color: #333;
  text-decoration: none;
  font-weight: 500;
  font-size: 14px;
  letter-spacing: 1px;
  transition: color 0.3s ease;
  position: relative;
  padding: 5px 0;
}

.nav-link:hover {
  color: #9c7a6b;
}

.nav-link.active {
  color: #9c7a6b;
}

.nav-link.active::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: #9c7a6b;
}

.header-actions {
  display: flex;
  align-items: center;
}

/* Botões */
.btn-cta {
  background: #9c7a6b;
  color: white;
  border: none;
  padding: 12px 25px;
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 1px;
  border-radius: 30px;
  cursor: pointer;
  transition: all 0.3s ease;
  text-transform: uppercase;
}

.btn-cta:hover {
  background: #7a5f53;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(156, 122, 107, 0.3);
}

.btn-outline {
  background: transparent;
  color: #9c7a6b;
  border: 2px solid #9c7a6b;
  padding: 10px 23px;
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 1px;
  border-radius: 30px;
  cursor: pointer;
  transition: all 0.3s ease;
  text-transform: uppercase;
  margin-left: 15px;
}

.btn-outline:hover {
  background: #9c7a6b;
  color: white;
  transform: translateY(-2px);
}

/* Menu Mobile */
.menu-toggle {
  display: none;
  background: none;
  border: none;
  width: 30px;
  height: 20px;
  flex-direction: column;
  justify-content: space-between;
  margin-left: 20px;
  cursor: pointer;
  padding: 0;
}

.menu-toggle span {
  display: block;
  width: 100%;
  height: 2px;
  background: #333;
  transition: all 0.3s ease;
}

.mobile-menu {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.95);
  z-index: 999;
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.mobile-menu.active {
  opacity: 1;
  visibility: visible;
}

.mobile-menu-inner {
  text-align: center;
}

.mobile-menu nav ul {
  list-style: none;
  padding: 0;
  margin: 0 0 30px;
}

.mobile-menu nav li {
  margin: 20px 0;
}

.mobile-menu .nav-link {
  font-size: 18px;
  color: #333;
  text-decoration: none;
}

/* Hero Section */
.hero {
  height: 100vh;
  position: relative;
  overflow: hidden;
}

.hero-slider {
  height: 100%;
}

.hero-slider .slide {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  opacity: 0;
  transition: opacity 1s ease;
}

.hero-slider .slide.active {
  opacity: 1;
}

.hero-content {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  max-width: 600px;
  color: white;
}

.hero-title {
  font-family: "Playfair Display", serif;
  font-size: 60px;
  font-weight: 700;
  line-height: 1.2;
  margin-bottom: 20px;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
}

.hero-title span {
  color: #e8d8d0;
}

.hero-subtitle {
  font-size: 18px;
  margin-bottom: 30px;
  text-shadow: 0 1px 3px rgba(0, 0, 0, 0.3);
}

.hero-actions {
  display: flex;
}

.hero-slider-controls {
  position: absolute;
  bottom: 50px;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 10;
}

.slider-prev,
.slider-next {
  background: none;
  border: none;
  color: white;
  font-size: 30px;
  cursor: pointer;
  opacity: 0.7;
  transition: opacity 0.3s ease;
}

.slider-prev:hover,
.slider-next:hover {
  opacity: 1;
}

.slider-dots {
  display: flex;
  margin: 0 20px;
}

.slider-dots span {
  display: block;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: white;
  opacity: 0.5;
  margin: 0 5px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.slider-dots span.active {
  opacity: 1;
  transform: scale(1.2);
}

.scroll-down {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  cursor: pointer;
  z-index: 10;
}

.scroll-down span {
  display: block;
  width: 20px;
  height: 20px;
  border-bottom: 2px solid white;
  border-right: 2px solid white;
  transform: rotate(45deg);
  animation: scrollDown 1.5s infinite;
}

@keyframes scrollDown {
  0% {
    opacity: 0;
    transform: rotate(45deg) translate(-10px, -10px);
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    transform: rotate(45deg) translate(10px, 10px);
  }
}

/* Seções */
.section-header {
  text-align: center;
  margin-bottom: 60px;
}

.section-title {
  font-family: "Playfair Display", serif;
  font-size: 40px;
  font-weight: 700;
  margin-bottom: 15px;
}

.section-title span {
  color: #9c7a6b;
}

.section-subtitle {
  font-size: 18px;
  color: #777;
  margin-bottom: 20px;
}

.divider {
  width: 50px;
  height: 3px;
  background: #9c7a6b;
  margin: 0 auto;
}

.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 100px 0;
}

/* Serviços */
.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
}

.service-card {
  background: white;
  border-radius: 10px;
  padding: 30px;
  text-align: center;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
}

.service-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
}

.service-icon {
  width: 80px;
  height: 80px;
  margin: 0 auto 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #f9f5f2;
  border-radius: 50%;
}

.service-icon img {
  width: 40px;
  height: 40px;
}

.service-title {
  font-family: "Playfair Display", serif;
  font-size: 22px;
  margin-bottom: 15px;
  color: #333;
}

.service-description {
  color: #777;
  font-size: 15px;
  line-height: 1.6;
  margin-bottom: 20px;
}

.btn-service {
  background: #f9f5f2;
  color: #9c7a6b;
  border: none;
  padding: 8px 20px;
  font-size: 13px;
  font-weight: 600;
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-service:hover {
  background: #e8d8d0;
}

/* Sobre */
.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 50px;
  align-items: center;
}

.about-image {
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

.about-image img {
  width: 100%;
  height: auto;
  display: block;
}

.about-text p {
  color: #777;
  line-height: 1.8;
  margin-bottom: 30px;
}

.about-features {
  margin: 40px 0;
}

.feature {
  display: flex;
  margin-bottom: 25px;
}

.feature-icon {
  width: 50px;
  height: 50px;
  background: #f9f5f2;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 20px;
  flex-shrink: 0;
  color: #9c7a6b;
  font-size: 20px;
}

.feature-text h4 {
  font-family: "Playfair Display", serif;
  margin-bottom: 5px;
  color: #333;
}

.feature-text p {
  color: #777;
  font-size: 14px;
  margin: 0;
}

/* Galeria */
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
}

.gallery-item {
  position: relative;
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
  aspect-ratio: 1;
}

.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.gallery-item:hover img {
  transform: scale(1.1);
}

.gallery-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(156, 122, 107, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.gallery-item:hover .gallery-overlay {
  opacity: 1;
}

.gallery-overlay i {
  color: white;
  font-size: 30px;
}

/* Depoimentos */
.testimonials-slider {
  overflow: hidden;
  position: relative;
}

.testimonials-track {
  display: flex;
  transition: transform 0.5s ease;
}

.testimonial {
  min-width: 100%;
  padding: 0 50px;
}

.testimonial-content {
  background: white;
  border-radius: 10px;
  padding: 40px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
  display: flex;
}

.testimonial-avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  overflow: hidden;
  margin-right: 30px;
  flex-shrink: 0;
}

.testimonial-avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.testimonial-text {
  flex: 1;
}

.testimonial-text p {
  font-style: italic;
  color: #555;
  line-height: 1.8;
  margin-bottom: 20px;
}

.testimonial-author h4 {
  font-family: "Playfair Display", serif;
  margin-bottom: 5px;
}

.testimonial-author span {
  color: #777;
  font-size: 14px;
}

.testimonial-rating {
  margin-top: 15px;
  color: #ffc107;
}

.testimonials-controls {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 30px;
}

/* Contato */
.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 50px;
}

.contact-info h2 {
  text-align: left;
}

.contact-details {
  margin: 40px 0;
}

.contact-item {
  display: flex;
  margin-bottom: 25px;
}

.contact-item i {
  width: 50px;
  height: 50px;
  background: #f9f5f2;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 20px;
  flex-shrink: 0;
  color: #9c7a6b;
  font-size: 20px;
}

.contact-item h4 {
  font-family: "Playfair Display", serif;
  margin-bottom: 5px;
  color: #333;
}

.contact-item p {
  color: #777;
  font-size: 14px;
  margin: 0;
  line-height: 1.6;
}

.social-links {
  display: flex;
  margin-top: 30px;
}

.social-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: #f9f5f2;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 15px;
  color: #9c7a6b;
  font-size: 18px;
  transition: all 0.3s ease;
}

.social-icon:hover {
  background: #9c7a6b;
  color: white;
}

.contact-form .form-group {
  margin-bottom: 20px;
}

.contact-form input,
.contact-form select,
.contact-form textarea {
  width: 100%;
  padding: 12px 20px;
  border: 1px solid #e8d8d0;
  border-radius: 5px;
  font-family: "Montserrat", sans-serif;
  font-size: 14px;
  transition: all 0.3s ease;
}

.contact-form input:focus,
.contact-form select:focus,
.contact-form textarea:focus {
  border-color: #9c7a6b;
  outline: none;
}

.contact-form textarea {
  resize: vertical;
  min-height: 100px;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

/* Rodapé */
.footer {
  background: #f9f5f2;
  padding: 80px 0 0;
}

.footer-content {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 50px;
  margin-bottom: 60px;
}

.footer-logo {
  margin-bottom: 20px;
}

.footer-logo p {
  color: #777;
  line-height: 1.6;
  margin-top: 20px;
}

.footer-links {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.links-column h4 {
  font-family: "Playfair Display", serif;
  margin-bottom: 20px;
  color: #333;
}

.links-column ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.links-column li {
  margin-bottom: 10px;
}

.links-column a {
  color: #777;
  text-decoration: none;
  transition: color 0.3s ease;
  font-size: 14px;
}

.links-column a:hover {
  color: #9c7a6b;
}

.footer-bottom {
  border-top: 1px solid #e8d8d0;
  padding: 20px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.footer-bottom p {
  color: #777;
  font-size: 14px;
  margin: 0;
}

.footer-legal {
  display: flex;
}

.footer-legal a {
  color: #777;
  text-decoration: none;
  font-size: 14px;
  margin-left: 20px;
  transition: color 0.3s ease;
}

.footer-legal a:hover {
  color: #9c7a6b;
}

/* Modais */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1001;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.modal-overlay.active {
  opacity: 1;
  visibility: visible;
}

.modal-container {
  max-width: 90%;
  max-height: 90vh;
  overflow-y: auto;
}

.modal {
  background: white;
  border-radius: 10px;
  padding: 40px;
  position: relative;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.2);
}

.modal-close {
  position: absolute;
  top: 20px;
  right: 20px;
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
  color: #777;
  transition: color 0.3s ease;
}

.modal-close:hover {
  color: #333;
}

.modal-title {
  font-family: "Playfair Display", serif;
  font-size: 28px;
  margin-bottom: 10px;
  color: #333;
}

.modal-subtitle {
  color: #777;
  margin-bottom: 30px;
}

/* Modal de Serviço */
.service-modal-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
}

.service-modal-image {
  border-radius: 8px;
  overflow: hidden;
}

.service-modal-image img {
  width: 100%;
  height: auto;
  display: block;
}

.service-details {
  display: flex;
  margin: 20px 0;
}

.service-details .detail {
  display: flex;
  align-items: center;
  margin-right: 30px;
  color: #777;
}

.service-details .detail i {
  margin-right: 8px;
  color: #9c7a6b;
}

.service-description {
  color: #777;
  line-height: 1.8;
  margin-bottom: 20px;
}

.service-benefits h4 {
  font-family: "Playfair Display", serif;
  margin-bottom: 15px;
  color: #333;
}

.service-benefits ul {
  list-style: none;
  padding: 0;
  margin: 0 0 30px;
}

.service-benefits li {
  position: relative;
  padding-left: 25px;
  margin-bottom: 10px;
  color: #777;
}

.service-benefits li::before {
  content: "✓";
  position: absolute;
  left: 0;
  color: #9c7a6b;
}

/* Modal de Galeria */
.gallery-modal-content {
  position: relative;
}

.gallery-modal-content img {
  max-width: 100%;
  max-height: 70vh;
  display: block;
  margin: 0 auto;
}

.gallery-prev,
.gallery-next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255, 255, 255, 0.7);
  border: none;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  font-size: 24px;
  color: #333;
  cursor: pointer;
  transition: all 0.3s ease;
}

.gallery-prev:hover,
.gallery-next:hover {
  background: white;
}

.gallery-prev {
  left: 20px;
}

.gallery-next {
  right: 20px;
}

/* WhatsApp Flutuante */
.whatsapp-float {
  position: fixed;
  bottom: 30px;
  right: 30px;
  width: 60px;
  height: 60px;
  background: #25d366;
  color: white;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30px;
  box-shadow: 0 5px 20px rgba(37, 211, 102, 0.3);
  z-index: 100;
  transition: all 0.3s ease;
}

.whatsapp-float:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(37, 211, 102, 0.4);
}

/* ==================== RESPONSIVO - MOBILE PREMIUM ==================== */

@media (max-width: 1200px) {
  /* Pré-ajustes para tablets */
  .hero-title {
    font-size: 52px;
  }

  .section-title {
    font-size: 36px;
  }

  .about-content,
  .contact-content {
    gap: 40px;
  }
}

@media (max-width: 992px) {
  /* Tablet e mobile landscape */
  .hero-title {
    font-size: 44px;
    line-height: 1.2;
  }

  .hero-subtitle {
    font-size: 16px;
  }

  .about-content,
  .contact-content,
  .service-modal-content {
    grid-template-columns: 1fr;
  }

  .about-image,
  .service-modal-image {
    max-width: 500px;
    margin: 0 auto 30px;
    order: -1;
  }

  .footer-content {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .footer-links {
    justify-content: center;
  }

  .social-links {
    justify-content: center;
  }
}

@media (max-width: 768px) {
  /* Mobile premium - principais ajustes */

  /* Header e Menu Hamburguer */
  .header {
    padding: 15px 0;
  }

  .header.scrolled {
    padding: 10px 0;
  }

  .main-nav {
    display: none;
  }

  .menu-toggle {
    display: flex;
    width: 28px;
    height: 22px;
    flex-direction: column;
    justify-content: space-between;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
    margin-left: 20px;
    z-index: 1001;
  }

  .menu-toggle span {
    display: block;
    width: 100%;
    height: 2px;
    background: #9c7a6b;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    transform-origin: center;
  }

  .mobile-menu-open .menu-toggle span:nth-child(1) {
    transform: translateY(10px) rotate(45deg);
  }

  .mobile-menu-open .menu-toggle span:nth-child(2) {
    opacity: 0;
  }

  .mobile-menu-open .menu-toggle span:nth-child(3) {
    transform: translateY(-10px) rotate(-45deg);
  }

  /* Menu Mobile Premium */
  .mobile-menu {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(249, 245, 242, 0.98);
    backdrop-filter: blur(10px);
    z-index: 999;
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0;
    visibility: hidden;
    transition: all 0.5s ease;
  }

  .mobile-menu.active {
    opacity: 1;
    visibility: visible;
  }

  .mobile-menu-inner {
    width: 90%;
    max-width: 400px;
    text-align: center;
    transform: translateY(20px);
    transition: transform 0.5s ease;
  }

  .mobile-menu.active .mobile-menu-inner {
    transform: translateY(0);
  }

  .mobile-menu nav ul {
    list-style: none;
    padding: 0;
    margin: 0 0 40px;
  }

  .mobile-menu nav li {
    margin: 25px 0;
    opacity: 0;
    transform: translateY(15px);
    transition: all 0.4s ease;
  }

  .mobile-menu.active nav li {
    opacity: 1;
    transform: translateY(0);
  }

  .mobile-menu nav li:nth-child(1) {
    transition-delay: 0.1s;
  }
  .mobile-menu nav li:nth-child(2) {
    transition-delay: 0.15s;
  }
  .mobile-menu nav li:nth-child(3) {
    transition-delay: 0.2s;
  }
  .mobile-menu nav li:nth-child(4) {
    transition-delay: 0.25s;
  }
  .mobile-menu nav li:nth-child(5) {
    transition-delay: 0.3s;
  }
  .mobile-menu nav li:nth-child(6) {
    transition-delay: 0.35s;
  }

  .mobile-menu .nav-link {
    font-size: 20px;
    color: #333;
    text-decoration: none;
    font-weight: 500;
    position: relative;
    padding: 5px 0;
    transition: color 0.3s ease;
  }

  .mobile-menu .nav-link:hover,
  .mobile-menu .nav-link.active {
    color: #9c7a6b;
  }

  .mobile-menu .nav-link.active::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 30px;
    height: 2px;
    background: #9c7a6b;
  }

  /* Hero Section */
  .hero {
    height: 90vh;
    min-height: 600px;
  }

  .hero-title {
    font-size: 38px;
  }

  .hero-content {
    padding: 0 20px;
    text-align: center;
  }

  .hero-actions {
    flex-direction: column;
    align-items: center;
  }

  .btn-outline {
    margin-left: 0;
    margin-top: 15px;
  }

  /* Seções */
  .container {
    padding: 80px 0;
  }

  .section-header {
    margin-bottom: 40px;
  }

  .section-title {
    font-size: 34px;
  }

  /* Testemunhos */
  .testimonial-content {
    flex-direction: column;
    padding: 30px;
  }

  .testimonial-avatar {
    margin: 0 auto 20px;
  }

  /* Rodapé */
  .footer-links {
    grid-template-columns: 1fr 1fr;
    gap: 40px 20px;
  }

  .links-column {
    text-align: center;
  }

  /* WhatsApp */
  .whatsapp-float {
    width: 56px;
    height: 56px;
    bottom: 25px;
    right: 25px;
  }
}

@media (max-width: 576px) {
  /* Mobile pequeno - ajustes finos */

  .hero-title {
    font-size: 32px;
  }

  .hero-subtitle {
    font-size: 15px;
  }

  .section-title {
    font-size: 28px;
  }

  .section-subtitle {
    font-size: 16px;
  }

  /* Formulários */
  .form-row {
    grid-template-columns: 1fr;
  }

  /* Rodapé */
  .footer-links {
    grid-template-columns: 1fr;
  }

  /* Modal */
  .modal {
    padding: 30px 20px;
    width: 95%;
  }

  .service-modal-content {
    grid-template-columns: 1fr;
  }

  /* Serviços */
  .services-grid {
    grid-template-columns: 1fr;
  }

  /* Galeria */
  .gallery-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (max-width: 400px) {
  /* Ajustes extras para telas muito pequenas */
  .hero-title {
    font-size: 28px;
  }

  .btn-cta,
  .btn-outline {
    width: 100%;
  }

  .modal-title {
    font-size: 24px;
  }

  .mobile-menu .nav-link {
    font-size: 18px;
  }
}
</style>
