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
                // Login
                let result = await axios.post('http://localhost:8000/login', {
                    email: 'martins@martins.lv',
                    password: '123456',
                })
                console.log(result.data)

                // Get user data
                let options = {
                    headers: {
                        authorization: 'Bearer ' + result.data.access_token
                    }
                }

                result = await axios.get('http://localhost:8000/user', options)
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
