<template>
    <div>
        <div class="row mt-5">
            <table class="table" style="height: 30rem;">
                <thead>
                    <tr>
                        <th scope="col" class="text-center baslik">{{ info[i].bas }}</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(notlar, index) in info[i].bilgi" :key="index">
                        <td class="text-center bilgi">{{ notlar }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <p class="float-right">{{ i + 1 }}/{{ info.length }}</p>
        <div class="mt-5 slayt_footer">
            <button type="button" class="btn btn-outline-secondary float-left" @click="nav('prev')">
                <span aria-hidden="true">&laquo;</span>
            </button>
            <button type="button" class="btn btn-outline-secondary float-left" @click="i = 0">İlk</button>
            <button
                type="button"
                class="btn btn-outline-secondary float-right"
                @click="nav('next')"
            >
                <span aria-hidden="true">&raquo;</span>
            </button>
            <button
                type="button"
                class="btn btn-outline-secondary float-right"
                @click="i = info.length - 1"
            >Son</button>
        </div>
    </div>
</template>

<script>
import { info } from './data'
export default {
    name: 'Slayt',
    data() {
        return {
            info: info,
            i: 0,
        }
    },
    watch: {},
    /* bu kısım çalışıtırııkcak */
    methods: {
        nav(side) {
            if (side === 'prev') {
                if (this.i === 0) {
                    this.i = 0
                } else {
                    this.i--
                }
            } else {
                if (this.i === this.info.length - 1) {
                    this.i = this.info.length - 1
                } else {
                    this.i++
                }
            }

            console.log(this.i)
        },
    },
}
</script>

<style scoped>
.baslik {
    font-size: 2rem;
}
.bilgi {
    font-size: 1.2rem;
    border: none;
}
.slayt_footer {
    border-top: 1px dotted #cccccc;
    padding: 1rem 0 5rem 0;
}
</style>
