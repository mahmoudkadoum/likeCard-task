<script setup>
import { RouterLink } from 'vue-router'
import { ref } from 'vue'

const email = ref('');
const showError = ref(false)
const isEmailVaild = ref(true)

const checkEmail = ()=> {
  showError.value = true
  if(email.value) {
    var mailformat = /^\w+([\\.-]?\w+)*@\w+([\\.-]?\w+)*(\.\w{2,3})+$/;
    if (email.value.match(mailformat)) {
    isEmailVaild.value = true
  } else {
    isEmailVaild.value = false
  }
}
};
</script>

<template>
<!-- Footer -->
<div class="footer">
    <div class="container">
        <div class="content">
            <div class="logo">
                <img src="../assets/logo-light.svg" alt="">
                <p>
                    Generate outside the box thinking with the possibility to targtet the low.
                </p>
                <div>
                    <input v-model="email" type="text" placeholder="Enter email...">
                    <button @click="checkEmail" >Submit</button>
                    <Transition>
                        <span v-if="showError && !email">Email Required!</span>
                    </Transition>
                    <Transition>
                        <span v-if="showError && !isEmailVaild && !!email">Email Not Vaild!</span>
                    </Transition>
                </div>
            </div>
            <div class="theColumn">
                <p>Why Choose Us?</p>
                <RouterLink class="link" to="/">Scale</RouterLink>
                <RouterLink class="link" to="/">Solutions</RouterLink>
                <RouterLink class="link" to="/">Our Competition</RouterLink>
                <RouterLink class="link" to="/">Channels</RouterLink>
                <RouterLink class="link" to="/">Events</RouterLink>
                <RouterLink class="link" to="/">Watch the Demo</RouterLink>
            </div>
            <div class="theColumn">
                <p>Company</p>
                <RouterLink class="link" to="/">Leadership</RouterLink>
                <RouterLink class="link" to="/">Careers</RouterLink>
                <RouterLink class="link" to="/">Investor Relations</RouterLink>
                <RouterLink class="link" to="/">Media Kit</RouterLink>
            </div>
            <div class="theColumn">
                <p>Resources</p>
                <RouterLink class="link" to="/">Community</RouterLink>
                <RouterLink class="link" to="/">Events</RouterLink>
                <RouterLink class="link" to="/">Help Center</RouterLink>
                <RouterLink class="link" to="/">Partners</RouterLink>
            </div>
        </div>
        <div class="copyRight">
            <p>© 2023 Lookscout. All Rights Reserved.</p>
        </div>
    </div>
</div>
</template>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.footer {
    padding-block: 4rem;
    background: var(--color-gray-950, #151B28);
}

.footer .container .content {
    display: flex;
    width: 100%;
    justify-content: space-between;
    flex-wrap: wrap;
    row-gap: 4rem;
}
.footer .container div:first-child > div{
    display: flex;
    gap: .75rem;
    flex-direction: column;
    width: 31%;
    flex-basis: 31%;
}
.footer .container div:first-of-type > div:first-of-type{
    width: 100%;
    flex-basis: 100%;
}
.footer .container div:first-of-type div:first-of-type img{
    width: 160px;
    height: 40px;
}
.footer .container div:first-of-type div:first-of-type p{
    color: var(--color-neutral-800, #A5ACBA);
    font-size: 16px;
    font-weight: 400;
    line-height: 24px;
    letter-spacing: -0.1px;
}

.footer .container div:first-of-type .logo {
    gap: 1rem;
}
.footer .container div:first-of-type .logo div {
    width: 100%;
    height: 46px;
    max-height: 46px;
    display: flex;
    flex-direction: row;
    gap: 0;
}

.footer .container div:first-of-type .logo div {
    position: relative;
}
.footer .container div:first-of-type .logo div span {
    font-weight: 700;
    color: var(--color-warnning, #ff4848);
    filter: drop-shadow(0px 0px 8px #000000);
    position: absolute;
    bottom: 0;
    left: 0;
    transform: translateY(110%);
    white-space: nowrap;
}

.footer .container div:first-of-type .logo div input{
background: var(--color-gray-600, #2C3444);
  color: var(--color-base-white, #FFF);
  border: none;
  outline: none;
  padding-block: .75rem;
  padding-inline: 1rem;
  border-bottom-left-radius: 6px;
  border-top-left-radius: 6px;
  flex-grow: 1;
}
.footer .container div:first-of-type .logo div button{
  padding-inline: 1.125rem;
  padding-block: 0.75rem;
  color: var(--color-base-white, #FFF);
  background: var(--color-primary, #437EF7);
  border-bottom-right-radius: 6px;
  border-top-right-radius: 6px;
    border: none;
  outline: none;
  cursor: pointer;
  transition: all .25s;
}
.footer .container div:first-of-type div:first-of-type button:hover{
  filter: brightness(.95);
}

.footer .container .content .theColumn {
color: var(--color-neutral-200, #F9F9F9);
font-size: 16px;
font-weight: 600;
line-height: 24px;
letter-spacing: -0.1px;
}
.footer .container .content .theColumn p{
    margin-bottom: .75rem;
color: var(--color-neutral-200, #F9F9F9);
font-size: 16px;
font-weight: 600;
line-height: 24px;
letter-spacing: -0.1px;
}
.footer .container .content .theColumn a{
color: var(--color-neutral-800, #A5ACBA);
font-size: 16px;
font-weight: 500;
line-height: 24px;
letter-spacing: -0.1px;
}

.footer .container .copyRight {
display: flex;
padding-top: 32px;
margin-top: 64px;
justify-content: center;
align-items: center;
border-top: 1px solid var(--color-gray-300, #2E3545);
}
.footer .container .copyRight p{
color: var(--neutral-800, #A5ACBA);
text-align: center;
font-size: 16px;
font-weight: 400;
line-height: 24px; /* 150% */
letter-spacing: -0.1px;
}

@media (min-width: 1024px) {
    .footer .container div:first-child > div{
        width: 12.5%;
        flex-basis: 12.5%;
    }
    .footer .container div:first-of-type > div:first-of-type{
        width: 25%;
        flex-basis: 25%;
    }
}

@media (max-width: 600px) {
.footer .container div:first-child > div{
    width: 48%;
    flex-basis: 48%;
}
.footer .container div:first-of-type > div:first-of-type{
    width: 100%;
    flex-basis: 100%;
}
}
</style>
