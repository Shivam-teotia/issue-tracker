<template>
    <div>
        <div class="flex-container" v-if="!authState.isLogin" >
            <div class="router-view">
                <router-view></router-view>
            </div>
            <div class="intro-box">
                <intro-box></intro-box>
            </div>
        </div>
        <div v-else >
            <router-view></router-view>
        </div>
    </div>
</template>

<script>

import IntroBox from './IntroBox.vue';
import { useAuthStore } from '../store/auth.js';


export default {
    
    components: {
        'intro-box' : IntroBox
    },

    setup() {
        
        const authState = useAuthStore();

        return {
            authState
        }
    },
}
</script>


<style scoped > 

.flex-container {
    display: flex;
    align-content: center;
    justify-content: center;
}

.router-view {
    width: 50vw;
}

.intro-box {
    width: 50vw;
}




.login-box {
  display: flex;
  /* width: 90em; */
  height: 100vh;
  min-height: 40em;
  /* border-radius: 20px; */
  background-color: #ffffff;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.025);
}

.login-box-formbox,
.login-box-quotebox {
  display: flex;
  flex-direction: column;
  justify-content: center;
  flex: 1 1 100%;
  padding: 4em 6em;
}

.login-box-quotebox {
  color: white;
  background-color: #2028eb;
  background-image: url('data:image/svg+xml;charset=UTF-8,<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="%235257f0" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M6 17.6l-2 -1.1v-2.5"></path><path d="M4 10v-2.5l2 -1.1"></path><path d="M10 4.1l2 -1.1l2 1.1"></path><path d="M18 6.4l2 1.1v2.5"></path><path d="M20 14v2.5l-2 1.12"></path><path d="M14 19.9l-2 1.1l-2 -1.1"></path><line x1="12" y1="12" x2="14" y2="10.9"></line><line x1="18" y1="8.6" x2="20" y2="7.5"></line><line x1="12" y1="12" x2="12" y2="14.5"></line><line x1="12" y1="18.5" x2="12" y2="21"></line><path d="M12 12l-2 -1.12"></path><line x1="6" y1="8.6" x2="4" y2="7.5"></line></svg>'), linear-gradient(to right top, #0f1396, #202199, #2d2d9c, #38389f, #4243a1, #4243a1, #4142a0, #4142a0, #36379d, #2b2b99, #1d1e95, #0a0f90);
  background-size: 125%;
  background-repeat: no-repeat;
  background-position: center left;
}

.login-box-signup a {
  color: #a0a4e3;
  font-weight: 600;
  text-decoration: inherit;
}
.login-box-signup a:hover, .login-box-signup a:focus {
  color: #0f1396;
}

.login-box-login {
  display: flex;
  flex-wrap: wrap;
  align-content: center;
  flex-grow: 1;
}
.login-box-login > * {
  width: 100%;
  flex-shrink: 0;
}

form > div {
  position: relative;
  padding: 1.5em 0;
}
form > div input {
  color: #bebebe;
  width: 100%;
  padding: 1.5em 2em;
  border: 1px solid #bebebe;
  border-radius: 5px;
}
form > div input.input-email, form > div input.input-password {
  background-repeat: no-repeat;
  background-position: right 1em top 1.25em;
}
form > div input.input-email {
  background-image: url('data:image/svg+xml;charset=UTF-8,<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="lightgrey" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><circle cx="12" cy="12" r="4"></circle><path d="M16 12v1.5a2.5 2.5 0 0 0 5 0v-1.5a9 9 0 1 0 -5.5 8.28"></path></svg>');
}
form > div input.input-password {
  background-image: url('data:image/svg+xml;charset=UTF-8,<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="lightgrey" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><rect x="5" y="11" width="14" height="10" rx="2"></rect><circle cx="12" cy="16" r="1"></circle><path d="M8 11v-4a4 4 0 0 1 8 0v4"></path></svg>');
}
form > div input:focus {
  outline-color: #2028eb;
  border-color: #2028eb;
}
form > div label {
  font-size: 0.85em;
  position: absolute;
  top: 1.25em;
  left: 1.5em;
  background: #ffffff;
  padding: 0 0.5em;
}
form > div:focus-within label {
  color: #2028eb;
  font-weight: 600;
}
form > div .btn {
  color: #ffffff;
  font-size: 1em;
  letter-spacing: 1px;
  line-height: 1;
  background-color: #2028eb;
  border-color: #2028eb;
  cursor: pointer;
  transition: all 500ms ease;
}
form > div .btn:hover, form > div .btn:focus {
  background-color: #0f1396;
  border-color: #0f1396;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
}

.alternate-text {
  display: flex;
  align-items: center;
  margin: 1.5em 0;
  text-align: center;
}
.alternate-text::before, .alternate-text::after {
  content: "";
  flex: 1;
  border-bottom: 1px solid #bebebe;
}
.alternate-text::before {
  margin-right: 1em;
}
.alternate-text::after {
  margin-left: 1em;
}

.alternate-boxes {
  display: flex;
  justify-content: space-between;
  gap: 1em;
  margin-top: 1.5em;
}

.alternate-box {
  color: #0f1396;
  text-align: center;
  width: 100%;
  padding: 10px 20px;
  border: 1.5px solid #3a0f96;
  border-radius: 5px;
  cursor: pointer;
  transition: all 500ms ease;
}
.alternate-box svg {
  transition: transform 500ms ease;
}
.alternate-box:hover {
  border-color: #bebebe;
  background-color: rgba(190, 190, 190, 0.25);
}
.alternate-box:hover svg {
  transform: scale(1.25);
}
.quote-container {
  padding: 1em 0;
  position: relative;
}
.quote-container::before {
  content: "";
  position: absolute;
  top: -4.5em;
  left: -0.65em;
  width: 3.5em;
  height: 3.5em;
  background-color: #93f8e0;
  border-radius: 100%;
}
.quote-container::after {
  content: "";
  position: absolute;
  top: 0;
  left: 15px;
  height: 100%;
  width: 2px;
  background-color: rgba(255, 255, 255, 0.25);
}

.quote {
  color: #ffffff;
  font-size: 7em;
  font-weight: 600;
  line-height: 1;
}

.quote-small {
  color: #ebeef7;
  line-height: 180%;
  padding: 2em 0 0 6em;
  position: relative;
}
.quote-small::before {
  content: "";
  position: absolute;
  top: 2.75em;
  left: 1.2em;
  width: 3em;
  height: 2px;
  background-color: rgba(255, 255, 255, 0.25);
}

</style>