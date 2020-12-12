<template>
  <div class="row q-pa-md q-gutter-md">
    <div class="col-12 col-md-6">
      <q-card class="rounded-border">
        <q-card-section class="bg-primary text-white">
          <div class="text-h6">Registrar Cliente</div>
        </q-card-section>
        <q-form @submit.prevent.stop="onSubmit">
          <q-input
            type="number"
            style
            filled
            v-model="cuit"
            label="CUIT"
            min=0
            :rules="[val => !!val || 'Campo obligatorio']"
          />
          <q-input
            v-model="nombre"
            filled
            label="Nombres"
            :rules="[val => !!val || 'Campo obligatorio']"
          />
          <q-input
            v-model="apellido"
            filled
            label="Apellido"
            :rules="[val => !!val || 'Campo obligatorio']"
            />
          
          <div class="row q-gutter-xs">
            <div class="col-12 col-md-4">
              <q-input
                v-model="localidad"
                filled
                label="Localidad"
                :rules="[val => !!val || 'Campo obligatorio']"
              />
            </div>
            <div class="col-12 col-md-4">
              <q-input
                v-model="calle"
                filled
                label="Calle"
                :rules="[val => !!val || 'Campo obligatorio']"
              />
            </div>
            <div class="col-12 col-md">
              <q-input
                type="number"
                v-model="altura"
                filled
                label="Altura"
                :rules="[val => !!val || 'Campo obligatorio']"
              />
            </div>
          </div>
          <q-card-actions align="right">
            <q-btn label="Guardar" type="submit" color="primary"></q-btn>
          </q-card-actions>
        </q-form>
      </q-card>
    </div>

    <div class="col-12 col-md">
      <q-card class="rounded-border">
        <q-card-section class="bg-primary text-white">
          <div class="text-h6">Listado de Clientes</div>
        </q-card-section>
        <q-list v-for="cliente in clientes" :key="cliente.cuit" bordered separator>
          <q-item-section class="q-pa-md" >
            <q-item-label>{{ cliente.nombreApellido }}</q-item-label>
            <q-item-label caption>{{ cliente.direccion }}</q-item-label>
          </q-item-section>
        </q-list>
      </q-card>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "Pedidos",
  data () {
    return {
      cuit: null,
      apellido: null,
      nombre: null, 
      localidad: null, 
      calle: null, 
      altura: null, 
      clientes: [
        {
          cuit: '20-14252352-1',
          nombreApellido: 'Martin Juarez',
          direccion: 'Entre Rios 1561, Rosario'
        },
        {
          cuit: '20-1525234-1',
          nombreApellido: 'Esteban Meier',
          direccion: 'Zeballos 200, Rosario'
        },
        {
          cuit: '27-28512493-3',
          nombreApellido: 'Elena Rodriguez',
          direccion: 'Entre Rios 1561, Rosario'
        },
        {
          cuit: '27-432534-5',
          nombreApellido: 'Martina Flores',
          direccion: 'Entre Rios 1561, Rosario'
        }
      ],
    }
  },

  methods: {
    onSubmit() { 
      let nuevoCliente = {
        cuit: this.cuit,
        nombreApellido: this.nombre + ' ' + this.apellido,
        direccion: this.calle + ' ' + this.altura + ', ' + this.localidad
      }
      this.clientes.push(nuevoCliente)
    },
  }
}
</script>

<style>
  .q-form {
    margin-left: 20px;
    margin-right: 20px;
    margin-top: 30px;
  }
</style>