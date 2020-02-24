<template>
    <div class='w3-block w3-black cust-full-page-screen-height'>
        <div class='w3-block w3-row w3-center w3-padding-16 cust-splash-text-size cust-splash-row-size'>
            <div class='w3-third w3-mobile'>
                <img
                    src='../assets/headshot.png'
                    class='w3-circle w3-image cust-splash-content-size'
                />
            </div>
            <div class='w3-rest w3-mobile w3-text-lime cust-splash-content-size'>
                <code v-html='displayHelloMessage' />
            </div>
        </div>
        <div class='w3-center'>
            <i
                class='material-icons cust-splash-nav-icon-size'
                > expand_more </i>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Splash',
    data: () => ({
        helloMessage: `Hi, I'm Mike!
        I do some cool stuff. Wanna see?
        `.split(''),
        displayHelloMessage: ``
    }),
    mounted() {
        this.updateDisplayHelloMessage()
    },
    methods: {
        updateDisplayHelloMessage() {
            this.displayHelloMessage += this.helloMessage.shift()
            this.displayHelloMessage = this.displayHelloMessage.replace('\n', '<br/>')
            if(this.helloMessage.length !== 0) {
                let timeout
                if((/[!.?]/).test(this.displayHelloMessage[this.displayHelloMessage.length-1])) {
                    timeout = 200
                }
                else if((/\S/).test(this.helloMessage[0])) {
                    timeout = 100
                }
                else if((/\s/).test(this.helloMessage[0])) {
                    timeout = 0
                }
                setTimeout(() => this.updateDisplayHelloMessage(),timeout)
            }
            else if(this.helloMessage.length !== 0 && (/\s/).test(this.helloMessage[0])) {
                this.updateDisplayHelloMessage()
            }
        }
    }
}
</script>