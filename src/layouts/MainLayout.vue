<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Probando Quasar
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Secciones
        </q-item-label>
        <Link
          v-for="link in links"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import Link from 'components/Link.vue'

const linksData = [
  {
    title: 'Inicio',
    caption: 'Página de Inicio',
    icon: 'home',
    link: '/'
  },
  {
    title: 'Clientes',
    caption: '',
    icon: 'backup_table',
    link: "/clientes"
  },
  {
    title: 'Resumen',
    caption: 'Resumen de pedidos',
    icon: 'analytics',
    link: "/resumen"
  },
];

export default {
  name: 'MainLayout',
  components: { Link },
  data () {
    return {
      leftDrawerOpen: false,
      links: linksData,
      dataClientes: [
        {
          cuit: '20-14252352-1',
          nombreApellido: 'Martin Juarez',
          direccion: 'Entre Rios 1561'
        },
        {
          cuit: '20-1525234-1',
          nombreApellido: 'Esteban Meier',
          direccion: 'Zeballos 200'
        },
        {
          cuit: '27-28512493-3',
          nombreApellido: 'Elena Rodriguez',
          direccion: 'Entre Rios 1561'
        },
        {
          cuit: '27-432534-5',
          nombreApellido: 'Martina Flores',
          direccion: 'Entre Rios 1561'
        }
      ],

      dataPedidos: [ 
        {
          numero: 0,
          nombreCliente: 'Martin Juarez',
          descArticulo: '9 de Oro x24', 
          cantidad: 10, 
          monto: 1200,
          estado: 'Entregado',
        },
        {
          numero: 1,
          nombreCliente: 'Martin Juarez',
          descArticulo: 'Yerba Mate x56 1kg', 
          cantidad: 50, 
          monto: 3500,
          estado: 'En camino'
        },
        {
          numero: 2,
          nombreCliente: 'Esteban Meier',
          descArticulo: 'Criollitas x64',
          cantidad: 100, 
          monto: 2000,
          estado: 'Retrasado',
        },
        {
          numero: 3,
          nombreCliente: 'Martina Flores',
          descArticulo: '9 de Oro x24', 
          cantidad: 20, 
          monto: 300,
          estado: 'Entregado',
        },
        {
          numero: 4,
          nombreCliente: 'Elena Rodriguez',
          descArticulo: '9 de Oro x24',
          cantidad: 10, 
          monto: 500,
          estado: 'Entregado',
        }
      ],     

    }
  }
}
</script>


<style>
row {
  margin: 3px
}
.rounded-border {
  border-radius: 20px
}
</style>
