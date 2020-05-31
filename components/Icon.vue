<template>
    <font-awesome-icon v-bind:icon="[prefix === undefined ? 'fas' : prefix, icon]">{{ text }}</font-awesome-icon>
</template>

<script>
import Vue from 'vue'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { library } from '@fortawesome/fontawesome-svg-core'
import { faBriefcase, faHome, faCommentDots, faUserAstronaut, faUser, faUserSecret, faUserGraduate, faUserNinja, faCog, faMoneyBillAlt, faExternalLinkAlt } from '@fortawesome/free-solid-svg-icons'
import { faTwitter, faLinkedin, faInstagram, faGithub } from '@fortawesome/free-brands-svg-icons'

library.add(faBriefcase)
library.add(faHome)
library.add(faCommentDots)
library.add(faUserAstronaut)
library.add(faUser)
library.add(faUserSecret)
library.add(faUserGraduate)
library.add(faUserNinja)
library.add(faCog)
library.add(faTwitter)
library.add(faLinkedin)
library.add(faInstagram)
library.add(faGithub)
library.add(faMoneyBillAlt)
library.add(faExternalLinkAlt)

Vue.component('font-awesome-icon', FontAwesomeIcon)

export default {
    props: {
        icon: String,
        text: String,
        prefix: String
    }
}

</script>