<!--Voici un à quoi ressemble un simple composant Vue-->
Vue.component('button-counter', {
<!--Data doit être une fonction-->
    data: function () {
        return {
            count: 0
        }
    },
    template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
})