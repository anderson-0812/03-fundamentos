<template>
    <div>
        <h1>Indecision</h1>
        <img v-if="img" :src="img" alt="bg">
        <div class="bg-dark"></div>
        <div class="indecision-container">
            <input type="text" placeholder="Hazme una pregunta" v-model="question">
            <p>Recuerda terminar con un signo de interrogacion (?)</p>

            <div v-if="isValidQuestion">
                <h2>{{ question }}</h2>
                <h1>{{ answer }}</h1>
            </div>
        </div>

    </div>
</template>

<script>

    export default {
        name: "Indecision",

        data (){
            return {
                question: "Sere millonario?",
                answer:null,
                img: null,
                // img: "https://previews.123rf.com/images/sergiimyronenko/sergiimyronenko1703/sergiimyronenko170300001/74821454-le%C3%B3n-rey-aislado-en-negro.jpg"
                isValidQuestion: false
            }
        },
        methods:{
            async getAnswer(){
                this.answer = 'Pensando...'

                let { answer, image } = await fetch('https://yesno.wtf/api').then( r => r.json() )
                // console.log(answer);

                switch(answer)
                {
                    case 'yes':
                        answer = 'Si!';
                        break;
                    case 'no':
                        answer = 'No!';
                        break;
                    case 'maybe':
                        answer = 'Quizas';
                        break;
                }

                this.answer = answer
                this.img = image
            }
        },
        watch: {
            // question es la propiedad reactiva que esta en el data no es una funcion  
            question( value, oldValue){
                // console.log({value, oldValue});
                // console.log(value.includes('?'));

                this.isValidQuestion = false;

                if ( !value.includes('?')) return;

                this.isValidQuestion = true;

                //  TODO: realizar peticion php
                // la mejor practica es llamar a una funcion 
                this.getAnswer()

            }
        }
    }

</script>

<style scoped>
/* // scoped hace que solo este css sea aplicado para este componente  */

    img, .bg-dark {
        height: 100vh;
        left: 0px;
        max-height: 100%;
        max-width: 100%;
        position: fixed;
        top: 0px;
        width: 100vw;
    }

    .bg-dark {
        background-color: rgba(0, 0, 0, 0.4);
    }

    .indecision-container {
        position: relative;
        z-index: 99;
    }
    
    input {
        width: 250px;
        padding: 10px 15px;
        border-radius: 5px;
        border: none;
    }
    input:focus {
        outline: none;
    }

    p {
        color: white;
        font-size: 20px;
        margin-top: 0px;
    }

    h1, h2 {
        color: white;
    }
    
    h2 {
        margin-top: 150px;
    }

</style>