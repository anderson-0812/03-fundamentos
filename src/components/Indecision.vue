<template>
    <div>
        <h1>Indecision</h1>
        <img src="https://previews.123rf.com/images/sergiimyronenko/sergiimyronenko1703/sergiimyronenko170300001/74821454-le%C3%B3n-rey-aislado-en-negro.jpg" alt="bg">
        <div class="bg-dark"></div>
        <div class="indecision-container">
            <input type="text" placeholder="Hazme una pregunta">
            <p>Recuerda terminar con un signo de interrogacion (?)</p>

            <div>
                <h2>Sere millonario?</h2>
                <h1>Si, No, Pensando...</h1>
            </div>
        </div>

    </div>
</template>

<script>

    export default {
        name: "Indecision",
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