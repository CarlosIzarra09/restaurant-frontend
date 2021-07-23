<template>
  <v-container id="upgrade" fluid tag="section">
    <v-row justify="center">
      <v-col cols="12" md="7" >
        <v-autocomplete
          filled
          solo
          hide-no-data
          hide-details="auto"
          append-icon="mdi-chevron-down"
          label="Buscar productos por categoría"
          item-text="name"
          item-value="id"
          
          return-object
          v-model="value"
          :items="items"
        >
          <template v-slot:item="data">
            
            <v-list-item-avatar tile size="40px">
              <v-container
                
                class="pa-0"
                :style="data.item.color"
              >
                <v-icon class="pa-3" size="20px" color="white"
                  >mdi-content-copy</v-icon
                >
              </v-container>
            </v-list-item-avatar>
            <v-list-item-content>
                <v-list-item-title v-html="data.item.name" class="display-1"></v-list-item-title>
            </v-list-item-content>
            
            <v-list-item-action>
              <h4 class="display-1" style="color:grey">{{data.item.cant}} productos 
                <v-icon size="30">mdi-chevron-right</v-icon>
              </h4>
            </v-list-item-action>

          </template>

        </v-autocomplete>
        <v-container v-show="value.name !== null" class="pa-0">
          <v-card height="50px">
            <v-row class="ma-0">
              <v-container
                class="pa-0 ma-0"
                style="width: 50px; height: 50px; background-color: DeepSkyBlue"
              >
                <v-icon class="pa-3" size="25px" color="white"
                  >mdi-content-copy</v-icon
                >
              </v-container>
              <v-card-title class="display-1">
                {{ value.name }}
              </v-card-title>
              <v-spacer></v-spacer>
              <v-card-title class="display-1" style="color: Grey"
                >{{ value.cant }} Productos
              </v-card-title>
              <v-icon class="mr-3 mt-1">mdi-apps</v-icon>
            </v-row>
          </v-card>
        </v-container>

        <v-container class="pa-0">
          <v-row dense>
            <v-col v-for="(i, index) in value.products" :key="index">
              <v-card
                min-height="100%"
                min-width="140px"
                class="ma-0 d-flex flex-column"
              >
                <v-card-title class="title">{{ i.title }}</v-card-title>
                <v-img
                  src="https://i.ytimg.com/vi/kG0qMD7Y9-w/maxresdefault.jpg"
                  aspect-ratio="1.7778"
                  class="ma-1"
                ></v-img>
                <v-spacer></v-spacer>
                <v-card-actions class="pa-0">
                  <v-btn tile block color="primary" style="height: 20px">
                    <h4 class="display-1">S/ {{ i.price }}</h4>
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
            <v-spacer v-if="value.cant % 2 !== 0"></v-spacer>
          </v-row>
        </v-container>
      </v-col>

      <v-col cols="12" md="5" >
        <v-container class="pa-0">

          <!-- No cliente seleccionado -->
          <v-card class="ma-0 " height="100%">
            
            <v-row class="ma-0">
              <v-btn tile block color="white" height="55px" class="ma-0">
                <v-icon size="25px" color="black">mdi-account-circle</v-icon>
                <v-card-title
                  class="display-1 text-capitalize"
                  style="color: black"
                  >Agregar cliente</v-card-title
                >
                <v-spacer></v-spacer>
                <v-icon size="35px" color="grey">mdi-chevron-down </v-icon>
              </v-btn>

              <v-container class="pa-0 overflow-auto" style="height:280px">
                <v-list>
                  <v-list-item  v-for="(item, i) in 10" :key="i" class="pr-0">
                    
                    <v-list-item-content>
                      <v-list-item-title class="display-1">{{i+1}} <span class="mr-5"></span>Hamburguesa de pollo</v-list-item-title>
                      <v-list-item-subtitle >

                        <span class="mr-8"></span>
                        <h4 class="d-inline display-1">Cantidad: </h4>

                        <v-btn  color="primary" x-small class="mx-0">
                          <v-icon size="15">
                            mdi-plus-thick 
                          </v-icon>
                        </v-btn>

                        <h4 class="d-inline display-1 ml-2">1</h4>

                        <v-btn  color="error" x-small class="ml-2">
                          <v-icon size="15">
                            mdi-minus-thick
                          </v-icon>
                        </v-btn>

                        
                      </v-list-item-subtitle>
                    
                    </v-list-item-content>

                    <v-list-item-action class="mx-0">
                      <v-btn 
                      color="grey"
                      style="background-color:white"
                      plain
                      x-small
                      class="mx-0"
                      height="40px"
                       >
                        
                        <h4 class="display-1" style="color:black">S/7.00</h4>
                        
                        <v-icon color="black" class="ml-3"> mdi-trash-can </v-icon>

                      </v-btn>
                    </v-list-item-action>
                  </v-list-item>
                </v-list>
              </v-container>
              
            </v-row>
            
            
            
            


            <v-divider ></v-divider>
            <v-container class="px-0 pb-6">
              
              <v-row class="my-0 mx-3">
                <v-text-field solo
                 placeholder="Agregar nota"
                 clearable
                 
                 hide-details="auto"
                 class="pb-2"
                >
                  <template v-slot:append-outer>
                    <v-icon size="30" color="primary">mdi-card-text</v-icon>
                  </template>
                </v-text-field>
              </v-row>
                  
              <v-row class="ma-0"> 
                <v-checkbox class="ml-3">
                  <template v-slot:label>
                    <h4 class="display-1" style="color:black">Para Enviar</h4>
                  </template>
                </v-checkbox>

                
                <v-text-field solo
                 dense
                 prepend-inner-icon="mdi-alpha-s-box-outline"
                 class="ml-3 mt-2"
                 placeholder="0.0"
                 style="width:20px"                 
                 hide-details="auto"
                ></v-text-field>

                <v-checkbox class="ml-3">
                  <template v-slot:label>
                    <h4 class="display-1" style="color:black">Adeuda</h4>
                  </template>
                </v-checkbox>

                
                <v-text-field solo
                 dense
                 prepend-inner-icon="mdi-alpha-s-box-outline"
                 class="ml-3 mr-3 mt-2"
                 placeholder="0.0"
                 style="width:20px"                 
                 hide-details="auto"
                ></v-text-field>
              </v-row>
       
              

              <v-row class="ma-0">

                <v-select
                  style="width:50%"
                  hide-details="auto"
                  placeholder="Metodo de pago"
                  :items="metodos"
                  solo
                  height="55px"

                />

                
                <v-btn width="50%" class="ma-0" tile color="white" height="55px"
                  >Guardar cuenta</v-btn
                >

                
              </v-row>

              <v-row class="mx-0">
                <h4 class="display-1 ml-10 primary--text">Sub Total</h4>
                <v-spacer></v-spacer>
                <h4 class="display-1 mr-10 primary--text">S/ 0.00</h4>
              </v-row>

              <v-row class="mx-0 mt-6">
                <h4 class="display-1 ml-10">Costo de envio</h4>
                <v-spacer></v-spacer>
                <h4 class="display-1 mr-10">S/ 0.00</h4>
              </v-row>

              <v-row class="mx-0 mt-6">
                <h4 class="display-1 ml-10">Comision IZI PAY 5%</h4>
                <v-spacer></v-spacer>
                <h4 class="display-1 mr-10">S/ 0.00</h4>
              </v-row>

              <v-row class="mx-3 mt-6">
                <v-btn class="mx-0" color="primary" block height="55px">
                  
                    <h4 class="display-1">Cobrar</h4>
                    <v-spacer></v-spacer>
                    <h4 class="display-1">S/ 0.00</h4>
                  
                </v-btn>
              </v-row>


            </v-container>
          </v-card>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    items: [
      {
        name: "Hamburguesas",
        color: {'background-color':'cyan'},
        id: 1,
        cant: 4,
        products: [
          {
            title: "De pollo",
            price: 4.5,
          },
          {
            title: "De carne",
            price: 4.5,
          },
          {
            title: "De Carne con huevo",
            price: 4.5,
          },
          {
            title: "Choriburguer",
            price: 4.5,
          },
        ],
      },
      {
        name: "Broster",
        color: {'background-color':'#03A9F4'},
        id: 2,
        cant: 5,
        products: [
          {
            title: "Alita",
            price: 4.5,
          },
          {
            title: "Piernita",
            price: 4.5,
          },
          {
            title: "Muslito",
            price: 4.5,
          },
          {
            title: "Pechito",
            price: 4.5,
          },
          {
            title: "dsadasd",
            price: 4.5,
          },
        ],
      },
    ],

    value: { name: null, color:null,id: null, cant: null, products: null },
    metodos:['Efectivo','Izi Pay','Yape'],
  }),
  methods: {},
};
</script>

<style scoped>
</style>