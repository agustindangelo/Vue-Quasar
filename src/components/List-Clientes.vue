<template>
  <q-card class="rounded-border">
    <q-card-section class="bg-primary text-white">
      <div class="text-h6">Listado de Clientes</div>
    </q-card-section>
    <transition-group
      appear
      enter-active-class="animated backInDown"
      leave-active-class="animated backInDown"
    >
    <q-list v-for="cliente in clientes" :key="cliente.cuit" bordered separator>
      <q-item>
        <q-item-section class="q-pa-md" >
          <q-item-label style="font-size: 17px">{{ cliente.nombreApellido }}</q-item-label>
          <q-item-label caption style="font-size: 15px">{{ cliente.direccion }}</q-item-label>
        </q-item-section>
        <q-item-section side>
            <q-icon name="delete" @click="eliminarCliente(cliente.cuit)"></q-icon>
        </q-item-section>
      </q-item>
    </q-list>
    </transition-group>
  </q-card>
</template>

<script>
export default {
  name: 'ListClientes',
  props: [ 'clientes' ],
  data () {
    return {
    }
  },
  methods: {
    eliminarCliente(cuit){
      this.$emit('eliminarCliente', cuit)
    }
  }
}
</script>

<style scoped>
.q-icon {
  color: #C10015;
}
.q-icon:hover{
  cursor: pointer;
  color: #970012 
}
</style>