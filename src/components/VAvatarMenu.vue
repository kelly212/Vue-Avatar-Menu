<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
			<div>
						<v-menu open-on-hover location="end" transition="scale-transition">
									<template v-slot:activator="{ props  }">
												<v-avatar v-bind:="props " :size="size"  class="text-left" :rounded="rounded">
															<v-img :src="exibirImagem(item, '50')" alt="avatar"></v-img>
												</v-avatar>
									</template>
									<v-card style="width: 300px">
												<v-card-title>
															<v-img :src="exibirImagem(item, '400')" alt="avatar" class="imgZoom" contain></v-img>
												</v-card-title>
									</v-card>
						</v-menu>
			</div>
</template>

<script>
   /* eslint-disable */

   import empty from '../assets/empty.jpg'
   export default {
      name: "VAvatarMenu",
						props:{
         item: {default: {urls_imagem: [], imagens: []}},
         size: {default: '25'},
         variant: {default: 'flat'}, // 'elevated' | 'flat' | 'tonal' | 'outlined' | 'text' | 'plain'
         rounded: {default: '0'}, // string | number | boolean
						},
      methods:{
         validarCampo(campo) {
            return (campo !== undefined && campo !== null && campo !== '')
         },
         selecionaImagem(urls, tamanho, anexoId) {
            let url
            let urlsPesquisa
            if (anexoId !== undefined) {
               let tempAnexo = urls.find(x => x.anexo === anexoId)
               if (tempAnexo !== null && tempAnexo !== undefined) {
                  urlsPesquisa = tempAnexo.urls
               }
            } else {
               if (urls !== undefined && urls.length > 0) {
                  let achou = urls.find(c => c.capa === 1)
                  if (achou !== undefined) {
                     urlsPesquisa = achou.urls
                  } else {
                     urlsPesquisa = urls[0].urls
                  }
               }
            }
            if (urlsPesquisa !== undefined && urlsPesquisa.length > 0) {
               url = urlsPesquisa.find(x => x.tamanho === tamanho)

               if (url === undefined) {
                  url = urlsPesquisa.find(x => x.tamanho === 'original')
               }
            } else {
               url = {
                  url: empty
               }
            }
            return url.url
         },

         exibirImagem(item, tam) {
            var src = empty
            if (this.validarCampo(item.urls_imagem) && item.urls_imagem.length >0) {
               src = this.selecionaImagem(item.urls_imagem, tam)
            } else {
               if (item.imagens !== undefined && item.imagens.length > 0) {
                  src = this.validarCampo(item.imagens[0].src) ?  item.imagens[0].src : item.imagens[0].url
               }
            }
            return src
         },
      }
   }
</script>
