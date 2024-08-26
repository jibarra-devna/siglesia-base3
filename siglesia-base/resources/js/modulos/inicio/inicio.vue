<template>
  <div class="titulo text-center">
      <h2 class="text-h2">Bienvenido(a) a <span class="text-h2"><b>SIGLESIA</b></span></h2>
      <p class="subtitle">Seleccione un módulo para acceder al sistema.</p>
    </div>

<VRow class="cards">
    <!-- Modulo Libros Parroquiales -->
    <VCol
      sm="6"
      cols="12"
    >
    <VCard class="borde text-center">
        <VCardText class="d-flex flex-column justify-center align-center">
          <VAvatar
            color="primary"
            variant="tonal"
            size="50"
            class="mb-4"
          >
            <VIcon
              size="2rem"
              icon="bx-book"
            />
          </VAvatar>

          <h4 class="text-h4">
            Libros Parroquiales
          </h4>
        </VCardText>
        <VCardText>
          <VBtn variant="elevated" to="/">
            Ingresar
          </VBtn>
        </VCardText>
      </VCard>
    </VCol>

    <!-- Modulo Agenda Parroquial -->
    <VCol
      sm="6"
      cols="12"
    >
    <VCard class="borde text-center">
        <VCardText class="d-flex flex-column justify-center align-center">
          <VAvatar
            color="primary"
            variant="tonal"
            size="50"
            class="mb-4"
          >
            <VIcon
              size="2rem"
              icon="bx-calendar"
            />
          </VAvatar>

          <h4 class="text-h4">
            Agenda Parroquial
          </h4>
        </VCardText>
        <VCardText>
          <VBtn variant="elevated" to="/">
            Ingresar
          </VBtn>
        </VCardText>
      </VCard>
    </VCol>

    <!-- Modulo Compras -->
    <VCol
      cols="12"
      md="6"
      lg="4"
    >
      <VCard class="borde text-center">
        <VCardText class="d-flex flex-column justify-center align-center">
          <VAvatar
            color="primary"
            variant="tonal"
            size="50"
            class="mb-4"
          >
            <VIcon
              size="2rem"
              icon="bx-cart"
            />
          </VAvatar>

          <h4 class="text-h4">
            Compras
          </h4>
        </VCardText>
        <VCardText>
          <VBtn variant="elevated" to="/">
            Ingresar
          </VBtn>
        </VCardText>
      </VCard>
    </VCol>

    <!-- Modulo Ventas -->
    <VCol
      cols="12"
      md="6"
      lg="4"
    >
      <VCard class="borde text-center">
        <VCardText class="d-flex flex-column justify-center align-center">
          <VAvatar
            color="primary"
            variant="tonal"
            size="50"
            class="mb-4"
          >
            <VIcon
              size="2rem"
              icon="bx-dollar"
            />
          </VAvatar>

          <h4 class="text-h4">
            Ventas
          </h4>
        </VCardText>
        <VCardText>
          <VBtn variant="elevated" to="/">
            Ingresar
          </VBtn>
        </VCardText>
      </VCard>
    </VCol>

    <!-- Modulo Inventario -->
    <VCol
      cols="12"
      md="6"
      lg="4"
    >
      <VCard class="borde text-center">
        <VCardText class="d-flex flex-column justify-center align-center">
          <VAvatar
            color="primary"
            variant="tonal"
            size="50"
            class="mb-4"
          >
            <VIcon
              size="2rem"
              icon="bx-box"
            />
          </VAvatar>

          <h4 class="text-h4">
            Inventario
          </h4>
        </VCardText>
        <VCardText>
          <VBtn variant="elevated" to="/">
            Ingresar
          </VBtn>
        </VCardText>
      </VCard>
    </VCol>
  </VRow>
</template>

<style lang="scss">
@use "@core-scss/template/pages/page-auth";

.cards {
  padding: 100px;
  padding-block-start: 40px;
}

.titulo {
  margin-block-start: 100px;
}

.borde {
  border-radius: 10px;
}

.borde:hover {
  border-block-end: 4px solid #5e72e4;
}

.subtitle {
  color: #6c757d;
  font-size: 18px;
}

</style>
