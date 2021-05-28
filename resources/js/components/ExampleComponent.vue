<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Example Component</div>

                    <div class="card-body">
                        I'm an example component.
                        <br>
                        <ul>
                        <li v-for="message in messages">
                            {{message}}
                        </li>
                        </ul>

                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                messages: [],
            }
        },
        mounted() {
            // console.log('Component mounted.')
            // console.log(window.location.hostname)//
            // Echo.join(`chat`)//
            // .here((users) => {//
            //     console.log(users);//
            // })//
            // .joining((user) => {//
            //     console.log(user.name+' se ha unido.');//
            // })//
            // .leaving((user) => {//
            //     console.log(user.name+' ha abandonado.');//
            // });//

            // Enable pusher logging - don't include this in production
            Pusher.logToConsole = true;

            var pusher = new Pusher('bb8ede7d732f9aba152a', {
                cluster: 'us2'
            });

            var channel = pusher.subscribe('my-channel');
            var olv = this.messages
            channel.bind('my-event', function(data) {
                console.log(data)
                olv.push(JSON.stringify(data));
            });

            // Vue application
            // const app = new Vue({
            // el: '#app',
            // data: {
            //     messages: [],
            // },
            // });
        }
    }
</script>
