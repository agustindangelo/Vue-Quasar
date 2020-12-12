<template>
  <q-page>
    <div class="row justify-center q-pa-md">
      <div class="col-6">
        <q-card flat bordered class="rounded-borders bg-grey-2">
          <q-card-section>
            <div class="row items-center no-wrap">
              <div class="col">
                <div class="text-h6">Bienvenido</div>
                <div class="text-subtitle2">Probando Quasar</div>
              </div>
            </div>
          </q-card-section>
          <q-separator />

          <div class="row">
            <div class="col">
              <q-card-actions class="justify-between">
                <q-btn flat to="/clientes">Ir a clientes</q-btn>
                <q-btn flat to="/resumen">Ir a resumen</q-btn>
              </q-card-actions>
            </div>
          </div>
        </q-card> 
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex'
}
</script>

<style scoped>
.rounded-borders{
  border-radius: 10px
}
</style>
