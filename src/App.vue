<template>
  <v-app theme="dark">

    <v-navigation-drawer temporary v-model="isDrawerOpen">
        <v-list>
          <v-list-subheader>Menu</v-list-subheader>
          <v-list-item prepend-icon="mdi-home">Home</v-list-item>
          <v-list-item prepend-icon="mdi-account">Usuário</v-list-item>

          <!-- encapsulamento do dropdown-->
          <v-list-group value="users">

            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-account-circle"
                title="Clientes"
              ></v-list-item>
            </template>

            <v-list-item prepend-icon="mdi-currency-usd">Faturamento</v-list-item>
            <v-list-item prepend-icon="mdi-chart-line">Relatorio</v-list-item>

          </v-list-group>
          <!-- encapsulamento do dropdown-->

        </v-list>

    </v-navigation-drawer>

    <v-app-bar>

      <v-app-bar-nav-icon @click="isDrawerOpen = !isDrawerOpen"/>
      <v-app-bar-title>
        APP
      </v-app-bar-title>  

      <template #append>

          <!-- esse icon do btn é só para o hover ficar redondo -->
          <v-btn icon class="mr-2">
            <v-badge dot color="info">
              <v-icon icon="mdi-bell-alert-outline"/>
            </v-badge>  
          </v-btn>

          <!-- encapsulamento do dropdown-->
          <v-menu>
            <template v-slot:activator="{ props }">
              <v-avatar v-bind="props">
                <v-img
                  cover
                  src="https://cdn-icons-png.flaticon.com/512/147/147142.png"
                  alt="John"
                />
              </v-avatar>
            </template>

            <v-card min-width="200px">
              <v-list :lines="false" density="compact" nav>

                <v-list-item prepend-icon="mdi-account-outline">
                  <v-list-item-title>Meu Perfil</v-list-item-title>
                </v-list-item>

                <v-list-item prepend-icon="mdi-heart-outline">
                  <v-list-item-title>Meu Perfil</v-list-item-title>
                </v-list-item>
                
              </v-list>
            </v-card>
            

          </v-menu>
          
         
      </template>
    </v-app-bar>

    <v-main>
      <v-container>
        <h1 class="mb-4">DashBoard</h1>

        <v-card flat class="border mb-4">

          <div class="d-flex justify-space-between">
            <v-card-title>Últimos Usuários</v-card-title>
            <v-card-title>

              <!-- encapsulamento da modal -->
              <v-dialog width="500px">
                <template #activator="{ props }">
                  <v-btn v-bind="props" variant="tonal" size="small">Adicionar Usuário</v-btn>
                </template>

                <v-card>
                  <v-card-title>Adicionar Usuário</v-card-title>
                  <v-card-text>
                    <v-row>

                      <v-col>
                        <v-text-field label="Nome" variant="outlined"></v-text-field>
                      </v-col>
                      
                      <v-col>
                        <v-text-field label="Email" 
                        variant="outlined"
                        :rules="emailRules"
                        ></v-text-field>
                      </v-col>
                     
                    </v-row>

                    <v-select label="Cargo" 
                    variant="outlined"
                    :items="['Admin', 'Gerente', 'Convidado']"
                    ></v-select>

                  </v-card-text>

                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn variant="tonal" class="mr-3">Cancelar</v-btn>
                    <v-btn variant="tonal" color="success" class="mr-3">Salvar</v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
              <!-- encapsulamento da modal -->
              
            </v-card-title>
            
          </div>

          
          <v-table>
            <thead>
              <tr>
                <th>Nome</th>
                <th>Email</th>
                <th>Cargo</th>
                <th>Ações</th>
              </tr>
            </thead>
              <tbody>
                <tr>
                  <td>Ciclano</td>
                  <td>Ciclano@gmail.com</td>
                  <td>
                    <v-chip color="primary" size="small" >Adminstrador</v-chip>
                  </td>
                  <td>
                    <v-btn variant="tonal" color="primary" >Editar</v-btn>
                  </td>
                </tr>
                <tr>
                  <td>Beltrano</td>
                  <td>Beltrano@gmail.com</td>
                  <td>
                    <v-chip color="success" size="small">Funcionario</v-chip>
                  </td>
                  <td>
                    <v-btn variant="tonal" color="primary" >Editar</v-btn>
                  </td>
                </tr>
                <tr>
                  <td>Fulano</td>
                  <td>Fulano@gmail.com</td>
                  <td>
                    <v-chip size="small">Convidado</v-chip>
                  </td>
                  <td>
                    <v-btn variant="tonal" color="primary" >Editar</v-btn>
                  </td>
                </tr>
                
              </tbody>
            </v-table>
        </v-card>
            

        <v-row >
          <v-col cols="12" md="4" lg="3">
            <v-card>

              <v-img 
                src="https://images.pexels.com/photos/3373939/pexels-photo-3373939.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                class="align-end text-while"
                >
                <v-card-title>
                  Top 10 Praias
                </v-card-title>
              </v-img>

              <v-card-subtitle class="pt-4">Rio de Janeiro</v-card-subtitle>

              <v-rating
                :model-value="4"
                color="amber"
                density="compact"
                half-increments
                readonly
                size="small"
                class="pl-4"
              />

              <v-card-text>
                <div>Rio de Janeiro</div>
                <div>Lorem ipsum dolor sit amet consectetur adipisicing elit. </div>
              </v-card-text>

              <v-card-actions>
                <v-btn variant="outlined" color="primary">Ver Mais</v-btn>
                <v-btn append-icon="mdi-cart" variant="tonal" color="warning">Comprar</v-btn>
              </v-card-actions>

            </v-card>
          </v-col>

          <v-col cols="12" md="4" lg="3">
            <v-card>

              <v-img 
                src="https://images.pexels.com/photos/1049298/pexels-photo-1049298.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                class="align-end text-while"
                >
                <v-card-title class="text-black">
                  Top 10 Praias
                </v-card-title>
              </v-img>

              <v-card-subtitle class="pt-4">Recife</v-card-subtitle>

              <v-rating
                :model-value="5"
                color="amber"
                density="compact"
                half-increments
                readonly
                size="small"
                class="pl-4"
              />

              <v-card-text>
                <div>Recife</div>
                <div>Lorem ipsum dolor sit amet consectetur adipisicing elit. </div>
              </v-card-text>

              <v-card-actions>
                <v-btn variant="outlined" color="primary">Ver Mais</v-btn>
                <v-btn append-icon="mdi-cart" variant="tonal" color="warning">Comprar</v-btn>
              </v-card-actions>

            </v-card>
          </v-col>

          <v-col cols="12" md="4" lg="3">
            <v-card>

              <v-img 
                src="https://images.pexels.com/photos/1174732/pexels-photo-1174732.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                class="align-end text-while"
                >
                <v-card-title class="text-black">
                  Top 10 Praias
                </v-card-title>
              </v-img>

              <v-card-subtitle class="pt-4" >Bahia</v-card-subtitle>

              <v-rating
                :model-value="4.5"
                color="amber"
                density="compact"
                half-increments
                readonly
                size="small"
                class="pl-4"
              />

              <v-card-text>
                <div>Bahia</div>
                <div>Lorem ipsum dolor sit amet consectetur adipisicing elit. </div>
              </v-card-text>

              <v-card-actions>
                <v-btn variant="outlined" color="primary">Ver Mais</v-btn>
                <v-btn append-icon="mdi-cart" variant="tonal" color="warning">Comprar</v-btn>
              </v-card-actions>

            </v-card>
          </v-col>

          <v-col cols="12" md="4" lg="3">
            <v-card>

              <v-img 
                src="https://images.pexels.com/photos/6652143/pexels-photo-6652143.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                class="align-end text-while"
                >
                <v-card-title>
                  Top 10 Praias
                </v-card-title>
              </v-img>

              <v-card-subtitle class="pt-4">Rio Grande do Norte</v-card-subtitle>

              <v-rating
                :model-value="4.5"
                color="amber"
                density="compact"
                half-increments
                readonly
                size="small"
                class="pl-4"
              />

              <v-card-text>
                <div>Rio Grande do Norte</div>
                <div>Lorem ipsum dolor sit amet consectetur adipisicing elit. </div>
              </v-card-text>

              <v-card-actions>
                <v-btn variant="outlined" color="primary">Ver Mais</v-btn>
                <v-btn append-icon="mdi-cart" variant="tonal" color="warning">Comprar</v-btn>
              </v-card-actions>

            </v-card>
          </v-col>
 
        </v-row>

        
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>

import { ref } from 'vue';

const isDrawerOpen = ref(false)

const emailRules = [
  value => {
    if(value) {
      return true
    }
    //else
    return "O Email é obrigatorio"
   
  },
  value => {
    if (value.includes('@')) {
      return true
    }
    //else
    return "Email Invalido"
  }
]


</script>
