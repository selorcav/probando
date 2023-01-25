<template>
    <div>
        <div v-for="separador in caracte">
            <div v-for="item in separador.items ">
                {{ item.marca }}
                {{ item.id }}
                <img :src="`https://www.pcfactory.cl/${item.thumbnail}`" alt="">
            </div>
            <!-- {{ separador  }} -->
        </div>
        <!-- <h2>{{ api.name }}</h2> -->
        <div>
            <!-- <h4>{{ caracte.name }}</h4>
            <img :src="caracte.sprites.front_default"  alt=""> -->
        </div>
    </div>
</template>

<script>
import axios from "axios";

    export default {
        data() {
            return {
                caracte: []
            }
        },
        props: { api: Object},
        methods: {
            consumirDatos: function (){
                // console.log(`https://pokeapi.co/api/v2/pokemon/${this.api.name}`)

                axios
                .get(`https://stoplight.io/mocks/modyo/pcfactory-documentation/79796109/campanas/ofertas-videojuegos/${this.api.dataSource.content}`)
                .then((res) => {
                    console.log(res.data)
                this.caracte = res.data;
                })
                .catch((e) => {
                console.log(e);
                });

            }
        },
        created: function () {
            this.consumirDatos();
        },
    }
</script>

<style scoped>

</style>