<script setup>
import { ref } from 'vue'
import Footer from '../components/AppFooter.vue'
import Model from '../components/CardPopup.vue'

import img1 from '../assets/img1.png'
import img2 from '../assets/img2.png'
import img3 from '../assets/img3.png'

import sec4_img1 from '../assets/sec4-img1.png'
import sec4_img2 from '../assets/sec4-img2.png'
import sec4_img3 from '../assets/sec4-img3.png'
import sec4_img4 from '../assets/sec4-img4.png'
import sec4_img5 from '../assets/sec4-img5.png'
import sec4_img6 from '../assets/sec4-img6.png'

const sectionTwoCardList = [
{
  id:1,
  src: img1,
  title: 'Reach your users with new tools',
  body: 'Efficiently unleash cross-media information without cross-media value. Quickly maximize.',
  extra: '25 Apr 2022 ',
},
{
  id:2,
  src: img2,
  title: 'Reach your users with new tools',
  body: 'Efficiently unleash cross-media information without cross-media value. Quickly maximize.',
  extra: '25 Apr 2022 ',
},
{
  id:3,
  src: img3,
  title: 'Reach your users with new tools',
  body: 'Efficiently unleash cross-media information without cross-media value. Quickly maximize.',
  extra: '25 Apr 2022 ',
}
];

const sectionFourCardList = [
{
  id:1,
  src: sec4_img1,
  title: 'Organize your digital assets with a methodology here and there.',
  extra: '25 Apr 2022 ',
},
{
  id:2,
  src: sec4_img2,
  title: 'Organize your digital assets with a methodology here and there.',
  extra: '25 Apr 2022 ',
},
{
  id:3,
  src: sec4_img3,
  title: 'Organize your digital assets with a methodology here and there.',
  extra: '25 Apr 2022 ',
},
{
  id:4,
  src: sec4_img4,
  title: 'Organize your digital assets with a methodology here and there.',
  extra: '25 Apr 2022 ',
},
{
  id:5,
  src: sec4_img5,
  title: 'Organize your digital assets with a methodology here and there.',
  extra: '25 Apr 2022 ',
},
{
  id:6,
  src: sec4_img6,
  title: 'Organize your digital assets with a methodology here and there.',
  extra: '25 Apr 2022 ',
}
];

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

const isOpen = ref(false)
const selectedCard = ref({})

    const togglePopup = (card) => {
        selectedCard.value = card
        isOpen.value = !isOpen.value
    };

  const setIsOpen = (value) => {
    isOpen.value = value
  };

</script>

<template>
  <main>
    <!-- Section 1 -->
    <div class="section-1">
      <p>1% OF THE INDUSTRY</p>
      <h1>Hype got you here. </h1>
      <h1>Stay for the support.</h1>
    </div>

    <!-- Section 2 -->
    <div class="section-2 container">
      <div class="first-card card">
        <img src="../assets/section-2-firstCard.png" alt="" srcset="" loading='lazy'>
        <div>
          <h3>Reach your users with new tools. Reach your users with new tools. Reach your users with new tools.</h3>
          <p>Efficiently unleash cross-media information without cross-media value. Quickly maximize.Efficiently unleash cross-media information without cross-media value. Quickly maximize.Efficiently unleash cross-media.</p>
          <p>25 Apr 2022 </p>
        </div>
      </div>
      <div class="cards">
        <div v-for="card in sectionTwoCardList" :key="card.id" class="card">
          <img :src="card.src" alt="" srcset="" loading='lazy'>
          <div>
            <h3>{{card.title}}</h3>
            <p>{{card.body}}</p>
            <p>{{card.extra}}</p>

          </div>
        </div>
      </div>
    </div>

    <!-- Section 3 -->
    <div class="section-3">
      <div class="container">
        <div>
          <h1>Welcome to your new digital reality that will rock your world.</h1>
          <p>
            Let us help you take you from zero to serious business and beyond.
            Our no-strings attached free trial lets you test our product today.
          </p>
        </div>
        <div>
          <div style="display: flex;flex-direction: column;gap:.5rem">
            <div>
              <input v-model="email" type="text" placeholder="Enter your email">
              <button @click="checkEmail">Submit</button>
              <Transition>              
              <span v-if="showError && !email">Email Required!</span>
              </Transition>
              <Transition>              
              <span v-if="showError && !isEmailVaild && !!email">Email Not Vaild!</span>
              </Transition>
            </div>
            <p>Subscribe to our newsletter</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Section 4 -->
    <div class="section-4 container">
      <h1>Latest Blog Posts</h1>
      <div class="cards">
        <div v-for="card in sectionFourCardList" :key="card.id" class="card">
          <img @click="togglePopup(card)" style="cursor: pointer;" :src="card.src" alt="" srcset="" loading='lazy'>
          <div>
            <p>{{card.extra}}</p>
            <h3>{{card.title}}</h3>
            <button @click="togglePopup(card)" style="cursor: pointer;">
              <p>Learn more</p>
              <img src="../assets/arrow-right.svg" height="20" width="20" alt="">
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Section 5 -->
    <div class="section-5">
      <div class="container">
      <div>
        <div class="content">
          <p>1% OF THE INDUSTRY</p>
          <h1>Welcome to your new digital reality that which will rock your world truly at all.</h1>
          <div style="display:flex;gap:.5rem">
            <button>Sign Up</button>
            <button>Log in</button>
          </div>
        </div>
      </div>
      </div>
    </div>

    <Footer />
    <Model :is-open="isOpen" :theCard="selectedCard" @set-is-open="setIsOpen"/>

  </main>
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

.section-1 {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding-inline: 30px;
  padding-block: 82px;
  background-color: var(--color-neutral-100, #F8F9FB);
}
.section-1 > * {
  text-align: center;
}
.section-1 p {
  font-weight: 600;
  font-size: 14px;
  line-height: 20px;
  letter-spacing: -.1px;
  color: var(--color-primary);
}
.section-1 h1 {
  font-weight: 700;
  font-size: 52px;
  line-height: 60px;
  color: var(--color-gray-200);
}

.section-2{
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
  padding-block: 4rem;
  max-width: 100vw;
}

.section-2 .card > div h3 {
  color: var(--color-gray-200, #272D37);
}
.section-2 .card > div p {
  color: var(--color-gray-50, #4F5B63);
  letter-spacing: -.1px;
  line-height: 24px;

}
.section-2 .card > div p:first-child {
  font-size: 1rem;
  font-weight: 400;
}
.section-2 .card > div p:nth-child(2) {
  font-size: 14px;
  font-weight: 500;
}

.section-2 .first-card > div {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.section-2 .first-card img {
  max-width: 100%;
  width: 100%;
}
.section-2 .cards {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}
.section-2 .cards .card {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.section-2 .first-card,.cards {
  flex: 1;
}


.section-3 {
  background-color: var(--color-primary-200, #2B63D9);
  padding-block: 4rem;
}

.section-3 .container {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.section-3 .container > div {
  flex: 1;
}

.section-3 .container > div:first-child{
display: flex;
flex-direction: column;
gap: 24px;
}
.section-3 .container > div:first-child h1{
color: var(--color-base-white, #FFF);
line-height: 42px;
font-weight: 600;
font-size: 2rem;
}
.section-3 .container > div:first-child p{
color: var(--color-primary-50, #B1CCFB);
}

.section-3 .container div:nth-child(2) {
  display: flex;
  flex-direction: column;
  gap: .5rem;
}

.section-3 .container div:nth-child(2) div {
  position: relative;
}
.section-3 .container div:nth-child(2) div  {
  position: relative;
}
.section-3 .container div:nth-child(2) div span {
  margin-left: 1rem;
  font-weight: 700;
  color: var(--color-warnning, #ff4848);
  filter: drop-shadow(0px 0px 8px #000000);
  position: absolute;
  top: 50%;
  right: -20px;
  transform: translate(100%, -50%);
}

.section-3 .container div:nth-child(2) div input{
  background-color: var(--color-base-white, #FFF);
  border: none;
  outline: none;
  padding-block: .75rem;
  padding-inline: 1rem;
  width: 20rem;
  border-bottom-left-radius: 6px;
  border-top-left-radius: 6px;
}
.section-3 .container div:nth-child(2) div button{
  padding-inline: 1.125rem;
  padding-block: 0.75rem;
  color: #FFFFFF;
  background: var(--color-primary);
  border-bottom-right-radius: 6px;
  border-top-right-radius: 6px;
    border: none;
  outline: none;
  cursor: pointer;
  transition: all .25s;
}
.section-3 .container div:nth-child(2) button:hover{
  filter: brightness(.95);
}
.section-3 .container div:nth-child(2) p{
color: var(--color-primary-50, #B1CCFB);
font-size: 14px;
line-height: 20px;
letter-spacing: -0.1px;
}

.section-4{
  display: flex;
  gap: 2.5rem;
  padding-block: 4rem;
  flex-direction: column;
}

.section-4 > h1 {
  color: var(--color-gray-200, #272D37);
  margin-bottom: 24px;
  width: 100%;
text-align: center;
font-size: 32px;
font-style: normal;
font-weight: 700;
line-height: 40px;
letter-spacing: -0.64px;
}

.section-4 .cards {
  display: flex;
  justify-content: space-between;
  row-gap: 2rem;
  flex-wrap: wrap;
}

.section-4 .cards .card {
  flex-basis: 45%;
  width: 45%;
}

.section-4 .cards .card > img{
  width: 100%;
}

.section-4 .cards .card h3{
color: var(--color-gray-200, #272D37);
font-size: 22px;
font-weight: 600;
line-height: 30px;
letter-spacing: -0.22px;
  padding: 0§;
}

.section-4 .cards .card p{
font-size: 14px;
font-weight: 500;
line-height: 20px;
letter-spacing: -0.1px;
color: var(--color-gray-50, #5F6D7E);
}
.section-4 .cards .card button{
  display: flex;
  width: 100%;
  gap: .25rem;
  align-items: center;
  background: transparent;
  border: none;
  outline: none;
  cursor: pointer;
  transition: all .25s;
  padding: 0;
}

.section-4 .cards .card button p{
  color: var(--color-primary, #437EF7);
  font-weight: 600;
}

.section-5 {
    background-color: var(--color-primary-200, #2B63D9);
  padding-block: 4rem;
}

.section-5 .container > div {
  width: 100%;
  display: flex;
  justify-content: center;
}
.section-5 .container .content{
  width: 75%;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.section-5 .container .content p{
  text-align: center;
  width: 100%;
  color: var(--color-base-white, #FFF);
  font-size: 14px;
  font-weight: 600;
  line-height: 20px;
  letter-spacing: -0.1px;
}
.section-5 .container .content h1{
  text-align: center;
  width: 100%;
  color: var(--color-base-white, #FFF);
  font-size: 32px;
  font-weight: 600;
  line-height: 42px;
  letter-spacing: -0.32px;
  margin-bottom: 2rem;
}
.section-5 .container .content div{
  justify-content: center;
  width: 100%;
  display: flex;
  gap: 1rem;
}
.section-5 .container .content div button{
  padding-inline: 1.125rem;
  padding-block: 0.75rem;
  border-radius: 6px;
  border: none;
  outline: none;
  cursor: pointer;
  transition: all .25s;
}
.section-5 .container .content div button{
  filter: brightness(.95);
}
  .section-5 .container .content div button:first-of-type{
    background: #FFFFFF;
    color: var(--color-primary);
  }
  .section-5 .container .content div button:nth-child(2){
    color: #FFFFFF;
    background: var(--color-primary);
  }

  @media (min-width: 1024px) {
  .section-1::before {
  transform: translateX(-50%);
  left: 50%;
  }

  .section-2 .cards .card {
  flex-direction: row;
}


  .section-2, .section-3 .container {
    flex-direction: row;
  }
  .section-3 .container div:nth-child(2) {
    justify-content: center;
    align-items: center;
  }

  .section-4 .cards .card {
  flex-basis: 31%;
  width: 31%;
}

.section-5 .container .content{
  width: 50%;

}
  }


  @media (min-width: 768px) and (max-width: 1023px) {
  .section-1::before {
  transform: translateX(-0%);
}
}


  @media (min-width: 600px) and (max-width: 767px) {
  .section-1::before {
  transform: translateX(-0%);
}
}


  @media (max-width: 600px) {
  .section-1::before {
  transform: translateX(-0%);
}
  .section-1 h1 {
  font-size: 36px;
  line-height: 44px;
}

.section-4 .cards .card {
  flex-basis: 100%;
  width: 100%;
}

.section-5 .container .content div{
  flex-direction: column;
  gap: 1rem;
}
}

</style>
