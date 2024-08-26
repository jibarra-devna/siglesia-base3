<script setup>
import NavItems from '@/layouts/components/NavItems.vue'
import logo from '@images/logo.svg?raw'
import logosiglesia from '@images/logo-comp.png'
import VerticalNavLayout from '@layouts/components/VerticalNavLayout.vue'
import Footer from '@/layouts/components/Footer.vue'
import NavbarThemeSwitcher from '@/layouts/components/NavbarThemeSwitcher.vue'
import UserProfile from '@/layouts/components/UserProfile.vue'

// Variables reactivas para fecha y hora
const currentDate = ref('')
const currentTime = ref('')

// Función para actualizar fecha y hora
const updateDateTime = () => {
  const now = new Date()

  const day = String(now.getDate()).padStart(2, '0')
  const month = String(now.getMonth() + 1).padStart(2, '0') // Enero es 0
  const year = now.getFullYear()

  let hours = now.getHours()
  const minutes = String(now.getMinutes()).padStart(2, '0')
  const ampm = hours >= 12 ? 'PM' : 'AM'
  hours = hours % 12
  hours = hours ? hours : 12 // El formato de 12 horas debe mostrar 12 en lugar de 0
  const strTime = hours + ':' + minutes + ' ' + ampm

  currentDate.value = `${day}/${month}/${year}`
  currentTime.value = strTime
}

onMounted(() => {
  // Actualiza cada segundo
  const interval = setInterval(updateDateTime, 1000)
  updateDateTime() // Llama inmediatamente para inicializar

  // Limpia el intervalo al desmontar el componente
  onBeforeUnmount(() => {
    clearInterval(interval)
  })
})
</script>

<template>
  <VerticalNavLayout>
    <!-- 👉 navbar -->
    <template #navbar="{ toggleVerticalOverlayNavActive }">
      <div class="d-flex h-100 align-center">
        <!-- 👉 Vertical nav toggle in overlay mode -->
        <IconBtn
          class="ms-n3 d-lg-none"
          @click="toggleVerticalOverlayNavActive(true)"
        >
          <VIcon icon="bx-menu" />
        </IconBtn>

        <!-- Fecha y hora actual -->
        <div class="me-2" style="padding-block-start: 17px;">
          <p>Bienvenido(a) a <b>SIGLESIA</b>, hoy es <b>{{ currentDate }}</b> y son las <b>{{ currentTime }}</b></p>
        </div>

        <VSpacer />

        <IconBtn
          href="https://github.com/themeselection/sneat-vuetify-vuejs-laravel-admin-template-free"
          target="_blank"
          rel="noopener noreferrer"
        >
          <VIcon icon="bxl-github" />
        </IconBtn>

        <IconBtn>
          <VIcon icon="bx-bell" />
        </IconBtn>

        <NavbarThemeSwitcher class="me-1" />

        <UserProfile />
      </div>
    </template>

    <template #vertical-nav-header="{ toggleIsOverlayNavActive }">
      <RouterLink
        to="/"
      >
      <div class="app-logo">
        <img :src="logosiglesia" alt="Logo" />
      </div>
      </RouterLink>

      <IconBtn
        class="d-block d-lg-none"
        @click="toggleIsOverlayNavActive(false)"
      >
        <VIcon icon="bx-x" />
      </IconBtn>
    </template>

    <template #vertical-nav-content>
      <NavItems />
    </template>

    <!-- 👉 Pages -->
    <slot />

    <!-- 👉 Footer -->
    <template #footer>
      <Footer />
    </template>
  </VerticalNavLayout>
</template>

<style lang="scss" scoped>
.meta-key {
  border: thin solid rgba(var(--v-border-color), var(--v-border-opacity));
  border-radius: 6px;
  block-size: 1.5625rem;
  line-height: 1.3125rem;
  padding-block: 0.125rem;
  padding-inline: 0.25rem;
}

.app-logo {
  display: flex;
  align-items: center; /* Alinea verticalmente si es necesario */
  justify-content: flex-start; /* Alinea los elementos a la izquierda */

  img {
    margin: -40px; /* Asegura que no haya margen que cause espaciado adicional */
    padding-inline-start: 140px; /* Asegura que no haya padding que cause espaciado adicional */
    transform: scale(0.3); /* Ajusta el tamaño del logo */
    transform-origin: left center; /* Alinea el punto de referencia para el escalado hacia la izquierda */
  }

  .app-logo-title {
    font-size: 1.25rem;
    font-weight: 500;
    line-height: 1.75rem;
    text-transform: uppercase;
  }
}
</style>
