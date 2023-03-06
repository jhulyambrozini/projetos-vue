<template>
    <div class="bg-teal-700 flex justify-center py-16 h-screen">
        <div class="w-1/3">
            <div class="p-4 text-right shadow-2xl rounded-t-lg bg-white">
                <p class="font-semibold text-gray-700 h-6">{{ operacao }}</p>
                <p class="font-bold text-3xl text-gray-900 my-2">{{ resultado }}</p>
            </div>


            <div class="grid grid-cols-4 grid-rows-5 shadow-2xl rounded-b-lg">
                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 col-span-2 hover:bg-teal-600" @click="clickAC()">AC</button>
                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="clickDEL()">DEL</button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800" @click="click('÷')">÷</button>

                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('7')">7</button>
                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('8')">8</button>
                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('9')">9</button>
                <button class="h-16 text-xl text-white font-semibold  bg-gray-700 border-gray-600 hover:bg-gray-800" @click="click('x')">x</button>

                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('4')">4</button>
                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('5')">5</button>
                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('6')">6</button>
                <button class="h-16 text-xl text-white font-semibold  bg-gray-700 border-gray-600 hover:bg-gray-800" @click="click('-')">-</button>

                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('1')">1</button>
                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('2')">2</button>
                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('3')">3</button>
                <button class="h-16 text-xl text-white font-semibold  bg-gray-700 border-gray-600 hover:bg-gray-800" @click="click('+')">+</button>

                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 col-span-2 hover:bg-teal-600 rounded-bl-lg" @click="click('0')">0</button>
                <button class="h-16 text-xl text-white font-semibold bg-teal-500 border-teal-400 hover:bg-teal-600" @click="click('.')">.</button>
                <button class="h-16 text-xl text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800 rounded-br-lg" @click="clickResultado()">=</button>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            operacao: '',
            resultado: '0'
        }
    },

    methods: {

        clickAC() {
            this.resultado = '0'
        },

        clickDEL() {
            if (this.resultado.length > 1) {
                this.resultado = this.resultado.substring(0, this.resultado.length -1)
            } else {
                this.resultado = '0'
            }
            this.operacao = ''
        },

        click(par) {
            if(this.resultado == '0'){
                this.resultado = par
            } else {
                this.resultado += par
            }
        },

        clickResultado() {
            let operacaoResultado = this.resultado
            this.operacao = operacaoResultado

            operacaoResultado = operacaoResultado.replace('x', '*')
            operacaoResultado = operacaoResultado.replace('÷', '/')
            this.resultado = eval(operacaoResultado)
        }
     }

}
</script>

<style>


button {
    border: 1px solid;
}


</style>