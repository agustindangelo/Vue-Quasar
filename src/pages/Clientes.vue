<template>
  <div class="row q-pa-md q-gutter-md">
    <div class="col-12 col-md-6">
      <q-card class="rounded-border">
        <q-card-section class="bg-primary text-white">
          <div class="text-h6">Registrar Cliente</div>
        </q-card-section>
        <q-form @submit.prevent.stop="onSubmit">
          <div class="row">
            <label>Datos Personales</label>
          </div>

          <div class="row q-gutter-md">
            <div class="col">
              <q-input
                v-model="nombre"
                filled
                label="Nombres"
                :rules="[val => !!val || 'Campo obligatorio']"
              />
            </div>
            <div class="col">
              <q-input
                v-model="apellido"
                filled
                label="Apellido"
                :rules="[val => !!val || 'Campo obligatorio']"
              />
            </div>
          </div>
          <div class="row q-gutter-md">
            <div class="col">
              <q-input
                type="number"
                style
                filled
                v-model="cuit"
                label="CUIT"
                min=0
                :rules="[val => !!val || 'Campo obligatorio']"
              />
            </div>
            <div class="col">
              <q-input filled label="Fecha de Nacimiento" v-model="fechaNacimiento" mask="date" :rules="['date']">
                <template v-slot:append>
                  <q-icon name="event" class="cursor-pointer">
                    <q-popup-proxy ref="qDateProxy" transition-show="scale" transition-hide="scale">
                      <q-date v-model="fechaNacimiento">
                        <div class="row items-center justify-end">
                          <q-btn v-close-popup label="Cerrar" color="primary" flat />
                        </div>
                      </q-date>
                    </q-popup-proxy>
                  </q-icon>
                </template>
              </q-input>
            </div>
          </div>
          
          <div class="row" style="margin-bottom: 10px"> 
            <q-separator inset/>
          </div>
          <div class="row">
            <label for="">Dirección</label>
          </div>

          <div class="row q-gutter-md">
            <div class="col-xs-4">
              <q-input
                v-model="localidad"
                filled
                label="Localidad"
                :rules="[val => !!val || 'Campo obligatorio']"
              />
            </div>
            <div class="col-xs-4">
              <q-input
                v-model="calle"
                filled
                label="Calle"
                :rules="[val => !!val || 'Campo obligatorio']"
              />
            </div>
            <div class="col-xs">
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
            <q-btn label="Guardar" type="submit" color="primary" style="width: 150px; margin-bottom: 15px" ></q-btn>
          </q-card-actions>
        </q-form>
      </q-card>
    </div>
    <div class="col">
      <list-clientes :clientes="clientes" @eliminarCliente="eliminarCliente($event)"></list-clientes> 
    </div>
   
  </div>
</template>

<script>
import ListClientes from '../components/List-Clientes.vue';

export default {
  components: { ListClientes },
  name: "Pedidos",
  data () {
    return {
      cuit: null,
      apellido: null,
      nombre: null, 
      localidad: null, 
      calle: null, 
      altura: null, 
      fechaNacimiento: null,
      clientes: [
        {
          cuit: '20-14252352-1',
          nombreApellido: 'Martin Juarez',
          direccion: 'Entre Rios 1561, Rosario',
          fechaNacimiento: '1990-11-20'
        },
        {
          cuit: '20-1525234-1',
          nombreApellido: 'Esteban Meier',
          direccion: 'Zeballos 200, Rosario',
          fechaNacimiento: '1998-8-15'
        },
        {
          cuit: '27-28512493-3',
          nombreApellido: 'Elena Rodriguez',
          direccion: 'Entre Rios 1561, Rosario',
          fechaNacimiento: '2000-11-20'
        },
        {
          cuit: '27-432534-5',
          nombreApellido: 'Martina Flores',
          direccion: 'Entre Rios 1561, Rosario',
          fechaNacimiento: '1976-11-20'
        }
      ],
    }
  },

  methods: {
    eliminarCliente(cuit){
      this.clientes.forEach(cliente => {
        if (cliente.cuit === cuit) {
          this.clientes.pop(cliente);
        }
      });
    },
    onSubmit() { 
      var yaRegistrado = false;
      this.clientes.forEach(cliente => {
        if (cliente.cuit.indexOf(this.cuit) != -1){
          yaRegistrado = true;
        }
      });
      if(yaRegistrado){
        this.$q.notify({
          type: 'negative',
          message: 'El CUIT ' + this.cuit + ' ya se encuentra registrado.'
        })
      } else {
        let nuevoCliente = {
          cuit: this.cuit,
          nombreApellido: this.nombre + ' ' + this.apellido,
          direccion: this.calle + ' ' + this.altura + ', ' + this.localidad,
          fechaNacimiento: this.fechaNacimiento
        }
        this.clientes.push(nuevoCliente);
        this.$q.notify({
          type: 'positive',
          message: 'El cliente se ha registrado'
        })
      }
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
  q-separator {
    margin-bottom: 10px;
    padding: 10px;
  }
  label {
    font-size: 20px;
    color:grey;
    margin-bottom: 10px
  }
</style>