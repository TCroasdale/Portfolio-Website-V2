<template>
    <font-awesome-icon v-bind:icon="icon">{{ text }}</font-awesome-icon>
</template>

<script>
import Vue from 'vue'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { library } from '@fortawesome/fontawesome-svg-core'
import { faBriefcase, faHome, faCommentDots, faUserAstronaut, faUser, faUserSecret, faUserGraduate, faUserNinja } from '@fortawesome/free-solid-svg-icons'

library.add(faBriefcase)
library.add(faHome)
library.add(faCommentDots)
library.add(faUserAstronaut)
library.add(faUser)
library.add(faUserSecret)
library.add(faUserGraduate)
library.add(faUserNinja)

Vue.component('font-awesome-icon', FontAwesomeIcon)

export default {
    props: {
        icon: String,
        text: String
    }
}

</script>