<script setup>
import { ref } from 'vue';

const sacerdotes = ref([
  {
    id_sacerdote: 1,
    titulo: 'Pbro. Lic.',
    nombre: 'Cristian Alejandro Conchas Mayorquín',
    fecha_nacimiento: '08/10/1980',
    inicio_periodo: '01/01/2020',
    fin_periodo: '-',
  },
  {
    id_sacerdote: 1,
    titulo: 'Diacono',
    nombre: 'Jorge Olmedo',
    fecha_nacimiento: '08/10/1980',
    inicio_periodo: '01/01/2020',
    fin_periodo: '-',
  },
]);

const sortKey = ref('');
const sortOrder = ref(1);

const sortTable = (key) => {
  if (sortKey.value === key) {
    sortOrder.value = -sortOrder.value;
  } else {
    sortKey.value = key;
    sortOrder.value = 1;
  }

  sacerdotes.value.sort((a, b) => {
    const result = a[key] < b[key] ? -1 : a[key] > b[key] ? 1 : 0;
    return result * sortOrder.value;
  });
};
</script>

<template>
  <div style="display: grid; grid-gap: 1.25rem; grid-template-columns: 1fr 1fr;">
    <h6 class="text-h6"><span class="subtitle text-h6">Configuración / </span> Sacerdotes</h6>
    <div style="text-align: end;">
      <a href="javascript:void(0);">
        <vBtn>
          <VIcon size="1rem" icon="bx-plus" />Añadir Sacerdote
        </vBtn>
      </a>
    </div>
  </div>
  <p></p>
  <vCard>
    <h5 class="titulos text-h5"><b>Gestionar Sacerdotes</b></h5>
    <VTable>
      <thead>
        <tr>
          <th @click="sortTable('titulo')">
            Título <i :class="sortKey === 'titulo' && sortOrder === 1 ? 'bx bx-chevron-up' : 'bx bx-chevron-down'"></i>
          </th>
          <th @click="sortTable('nombre')">
            Sacerdote <i :class="sortKey === 'nombre' && sortOrder === 1 ? 'bx bx-chevron-up' : 'bx bx-chevron-down'"></i>
          </th>
          <th @click="sortTable('fecha_nacimiento')">
            Fecha Nacimiento <i :class="sortKey === 'fecha_nacimiento' && sortOrder === 1 ? 'bx bx-chevron-up' : 'bx bx-chevron-down'"></i>
          </th>
          <th @click="sortTable('inicio_periodo')">
            Inicio Periodo <i :class="sortKey === 'inicio_periodo' && sortOrder === 1 ? 'bx bx-chevron-up' : 'bx bx-chevron-down'"></i>
          </th>
          <th @click="sortTable('fin_periodo')">
            Fin Periodo <i :class="sortKey === 'fin_periodo' && sortOrder === 1 ? 'bx bx-chevron-up' : 'bx bx-chevron-down'"></i>
          </th>
          <th>
            Acciones
          </th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="item in sacerdotes" :key="item.id_sacerdote">
          <td>{{ item.titulo }}</td>
          <td>{{ item.nombre }}</td>
          <td>{{ item.fecha_nacimiento }}</td>
          <td>{{ item.inicio_periodo }}</td>
          <td>{{ item.fin_periodo }}</td>
          <td class="icono">
        <router-link
        to="/">
        <VIcon
              size="1rem"
              icon="bx-pencil"
            />
        </router-link>
        &nbsp;
        <router-link
        to="/">
        <VIcon
              size="1rem"
              icon="bx-trash"
            />
        </router-link>
        </td>
        </tr>
      </tbody>
    </VTable>
  </vCard>
</template>

<style>
.titulos {
  padding: 20px;
}

.subtitle {
  color: #6c757d;
  font-size: 18px;
}

.dropdown-menu {
  min-inline-size: 150px;
}

.icono {
  align-items: center;
}
</style>
