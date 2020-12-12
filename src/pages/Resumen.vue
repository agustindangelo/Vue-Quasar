<template>
  <div class="row q-pa-md q-gutter-md"> 
    <div class="col-12 col-md-6">
      <q-table
        class="rounded-border"
        title="Pedidos"
        :data="dataPedidos"
        :columns="columnasPedidos"
        row-key="numero"
      />
    </div>
    <div class="col-12 col-md">
      <q-table
        class="rounded-border"
        title="Clientes"
        :data="dataClientes"
        :columns="columnasClientes"
        row-key="cuit"
      />
    </div>
 </div>
</template>

<script>
export default {
  name: 'Resumen',
  data () {
    return {
      columnasPedidos: [ 
        {
          name: 'numeroPedido',
          label: 'Número',
          field: 'numero',
          required: true,
          align: 'left',
          sortable: true,
          format: (val, row) => `# ${val}`,
          headerStyle: 'width: 200px',
        },
        { name: 'nombreCliente', label: 'Cliente', field: 'nombreCliente', sortable: true },
        { name: 'descArticulo', label: 'Artículo', field: 'descArticulo', sortable: true },
        { name: 'cantidad', label: 'Cantidad', field: 'cantidad', sortable: true, sort: (a, b) => parseInt(a, 9) - parseInt(b, 10) },
        { name: 'estado', label: 'Estado', field: 'estado', sortable: false}
      ],
      columnasClientes: [ 
        {
          name: 'cuit',
          label: 'CUIT',
          field: 'cuit',
          required: true,
          align: 'left',
          sortable: true,
          format: (val, row) => `# ${val}`,
          headerStyle: 'width: 200px',
        },
        { name: 'nombreApellido', label: 'Nombre y Apellido', field: 'nombreApellido', sortable: true },
        { name: 'direccion', label: 'Dirección', field: 'direccion', sortable: true },
      ],

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
  },
}
</script>

<style>
q-table{
  height: 400px;
}
.q-table__top,
.q-table__bottom,
thead tr:first-child th {
    /* bg color is important for th; just specify one */
  background-color: #f8efea
}
td:first-child{
  background-color: #fbe0c3
}
</style>