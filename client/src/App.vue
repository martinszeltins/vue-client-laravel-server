<template>
    My app
</template>

<script>
    import axios from 'axios'
    axios.defaults.withCredentials = true

    export default {
        methods:
        {
            async fetchData()
            {
                await axios.get('http://localhost:8000/sanctum/csrf-cookie')

                await axios.post('http://localhost:8000/login', {
                    email: 'martins@martins.lv',
                    password: '12345678',
                })

                const result = await axios.post('http://localhost:8000/api/user')
                console.log(result.data)
            },
        },
        
        created()
        {
            this.fetchData()
        },
    }
</script>

<style>
    html, body {
        background: #202125;
        color: #898a8d;
    }
</style>
