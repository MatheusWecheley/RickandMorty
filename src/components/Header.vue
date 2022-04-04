<template>
    <footer>
        <div class="container">
            <div class="navegation">
                <h2>Feito por: Matheus Wecheley</h2>
                <span><a href="https://www.instagram.com/maath_leal/">Instagram</a></span>
                <span><a href="https://github.com/Merveruz">GitHub</a></span>
                <span><a href="https://www.linkedin.com/in/matheus-leal-745237214/">LinkedIn</a></span>
            </div>
        </div>
    </footer>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style scoped>
  
.container {
    align-items: center;
    background-color: #1f1f23;
    display: flex;
    justify-content: center;
    text-align: center;
}

.navegation {
    margin-top: 20px;
    color: #62cc28;
    display: flex;
    flex-direction: column;
    padding: 20px;
}

span {
    margin-top: 20px;
    font-size: 27px;
}

a {
    color: #00d4ff;
    text-decoration: none;
}

</style>