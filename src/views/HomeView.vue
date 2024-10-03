<template>
			<div>
						<v-container>
									<br>
									<div style="text-align: center">
												<h1>Vue Avatar Menu</h1>
												<br>
									</div>
									<v-row justify="center">
												<v-col cols="4">
															<v-avatar-menu :item="item" size="40" variant="flat" rounded="0"></v-avatar-menu>
												</v-col>
									</v-row>
						</v-container>
			</div>
</template>

<script>
   import {defineComponent} from 'vue';

   // Components
   import VAvatarMenu from '../components/VAvatarMenu.vue';

   export default defineComponent({
      name: 'HomeView',
      data: () => ({
         item: {
            urls_imagem:[
               {
                  "anexo": "52c94d54-a9c0-4599-8f0e-2d391bb4c010",
                  "nome": "52c94d54-a9c0-4599-8f0e-2d391bb4c010_original.jpg",
                  "capa": true,
                  "urls": [
                     {
                        "tamanho": "50",
                        "url": "https://picsum.photos/seed/picsum/200/100"
                     },
                     {
                        "tamanho": "original",
                        "url": "https://picsum.photos/seed/picsum/600/400"
                     }
                  ]
               }
												],
            imagens:[{src:'https://picsum.photos/seed/picsum/400/300'}],
									}
						}),

      components: {
         VAvatarMenu,
      },
   });
</script>
