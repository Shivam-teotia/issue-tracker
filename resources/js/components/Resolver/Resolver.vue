<template>
  <main class="flex w-full h-full shadow-lg section dark:bg-black">
    <section class="flex flex-col w-3/12 bg-slate-800 dark:z-1">
      <div
        class="w-16 ms-5 mt-8 mb-9 pt-3 py-2 px-10 bg-blue-600 rounded-1xl rounded-ee-5xl text-white"
      >
        <p class="mt-1 text-3xl font-bold dark:text-white ms-6 mb-4">RESOLVER PANEL</p>
        <div class="ms-13">
          <DarkModeSwitcher :role="'resolver'" />
        </div>
      </div>

      <nav class="relative flex flex-col items-center">
        <div
          class="flex space-x-3 items-center justify-center pt-4 border-t-2 border-b-2 w-full h-18 border-white dark:border-blue-500 my-2 me-1"
        >
          <button
            @click="getResolvedTickets"
            class="w-10 p-1 border text-gray-700 bg-white hover:bg-slate-400 rounded-2xl mb-4 dark:bg-blue-500"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="1"
                d="M5 5a2 2 0 012-2h10a2 2 0 012 2v16l-7-3.5L5 21V5z"
              />
            </svg>
          </button>
          <p class="text-white text-xl mb-4">Resolved Tickets</p>
        </div>

        <div
          class="flex space-x-3 items-center justify-center pt-2 border-b-2 w-full h-15 border-white dark:border-blue-500 my-2 me-1"
        >
          <button
            @click="getProcessingTickets"
            class="w-10 p-1 ms-2 border text-gray-700 rounded-2xl bg-white hover:bg-slate-400 mb-4 dark:bg-blue-500"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="1"
                d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
              />
            </svg>
          </button>
          <p class="text-white text-xl mb-4">Processed Tickets</p>
        </div>

        <div
          class="flex space-x-3 items-center justify-center pt-2 border-b-2 w-full h-15 border-white dark:border-blue-500 my-2 me-3"
        >
          <button
            @click="getPendingTickets"
            class="w-10 p-1 border bg-white hover:bg-slate-500 text-gray-700 rounded-2xl mb-4 dark:bg-blue-500"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="1"
                d="M3 7v10a2 2 0 002 2h14a2 2 0 002-2V9a2 2 0 00-2-2h-6l-2-2H5a2 2 0 00-2 2z"
              />
            </svg>
          </button>
          <p class="text-white text-xl mb-4">Pending Tickets</p>
        </div>

        <div
          class="flex space-x-3 items-center justify-center pt-2 border-b-2 w-full h-15 border-white dark:border-blue-500 my-2 me-2.5"
        >
          <button
            @click="getRejectedTickets"
            class="w-10 p-1 border bg-white text-gray-700 hover:bg-slate-500 rounded-2xl mb-4 dark:bg-blue-500"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="1"
                d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"
              />
            </svg>
          </button>
          <p class="text-white text-xl mb-4">Rejected Tickets</p>
        </div>
      </nav>
      <!-- <router-link
        :to="`/resolver-profile/${$route.params.id}`"
        class="mt-2 text-white text-lg font-bold hover:text-blue-500"
      >
        
      </router-link> -->
      <div
        class="flex text-white justify-center space-x-2 bg-blue-500 hover:bg-blue-600 w-full mt-6 h-20"
      >
        <div class="focus:outline-none focus:border-transparent mt-2">
          <router-link :to="`/resolver-profile/${$route.params.id}`" class="w-full">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 22 22"
              stroke-width="1.5"
              stroke="currentColor"
              class="h-10 w-10 text-white-500 dark:text-slate-800"
              width="36"
              height="36"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M17.982 18.725A7.488 7.488 0 0 0 12 15.75a7.488 7.488 0 0 0-5.982 2.975m11.963 0a9 9 0 1 0-11.963 0m11.963 0A8.966 8.966 0 0 1 12 21a8.966 8.966 0 0 1-5.982-2.275M15 9.75a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"
              />
            </svg>
          </router-link>
        </div>
        <div class="h-8 w-26 mt-3 text-lg dark:text-black-2 mt-4">My Profile</div>
      </div>
      <div
        v-if="!logoutLoading"
        class="flex text-white justify-center items-center space-x-2 bg-red w-full pt-1 h-20"
      >
        <button @click="logoutHandler" class="focus:outline-none focus:border-transparent mb-1">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="h-8 w-8 text-white-500 dark:text-slate-800"
            width="24"
            height="24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M8.25 9V5.25A2.25 2.25 0 0 1 10.5 3h6a2.25 2.25 0 0 1 2.25 2.25v13.5A2.25 2.25 0 0 1 16.5 21h-6a2.25 2.25 0 0 1-2.25-2.25V15m-3 0-3-3m0 0 3-3m-3 3H15"
            />
          </svg>
        </button>
        <div class="h-8 w-26 text-lg dark:text-slate-900">LogOut</div>
      </div>
      <div
        v-if="logoutLoading"
        class="flex text-white justify-center space-x-2 bg-red w-full h-20 pt-4"
      >
        <Loader />
      </div>
    </section>
    <PageLoader v-if="loadingTickets" />
    <section
      v-if="!loadingTickets"
      class="flex flex-col pt-3 w-4/12 bg-grey-100 h-full overflow-y-scroll z-2 dark:bg-black dark:text-white"
    >
      <p class="text-xl font-semibold mt-2" align="center">
        {{ ticketStatus !== '' ? capitalizeFirstLetter(ticketStatus) + ' Tickets' : '' }}
      </p>
      <ul v-for="item in cards" :key="item" class="mt-5">
        <li
          @click="() => setAttributes(item)"
          class="py-5 border-b px-3 transition hover:bg-indigo-100 dark:hover:bg-slate-700 dark:hover:text-white"
        >
          <div class="flex justify-between items-center">
            <h3 class="text-lg font-semibold">
              {{ item.data.attributes.user.data.attributes.name }}
            </h3>
            <p class="text-md text-gray-400 text-right mb-3">
              {{ item.data.attributes?.created_at }}
            </p>
          </div>
          <div class="text-md italic text-gray-400">
            {{ item.data.attributes.title }}
          </div>
        </li>
      </ul>
      <div
        v-if="cards.length === 0"
        class="flex justify-between items-center h-full text-3xl ml-24"
      >
        No tickets are there :)
      </div>
    </section>
    <section
      v-if="!loadingTickets && cards.length !== 0"
      class="w-5/12 px-4 flex flex-col bg-white rounded-r-1xl overflow-y-auto dark:bg-black dark:text-white"
    >
      <!-- <div v-if="!username" class="flex justify-between items-center h-full text-3xl ml-8">
        No Ticket Selected
      </div> -->
      <div v-show="username" class="flex justify-between items-center h-48 border-b-2 mb-8">
        <div class="flex space-x-4 mt-8 pb-4 items-center">
          <div class="h-12 w-12 rounded-full overflow-hidden">
            <img :src="profile" loading="lazy" class="h-full w-full object-cover" />
          </div>
          <div class="flex flex-col">
            <h3 class="font-semibold text-lg">{{ username }}</h3>
            <p class="text-light text-gray-400">{{ email }}</p>
          </div>
        </div>
      </div>
      <section v-show="username">
        <h1 class="font-bold text-2xl">{{ title }}</h1>
        <article class="mt-8 text-gray-500 leading-7 tracking-wider dark:text-white">
          <p>
            {{ body }}
          </p>
          <!-- <footer class="mt-6">
            <p>Thanks & Regards,</p>
            <p>{{ username }}</p>
          </footer> -->

          <div v-if="ticketStatus !== 'pending'">
            <p class="text-black font-bold mt-8 text-xl dark:text-white">Resolver response</p>
            <p class="text-black font-bold dark:text-white">Feedback: {{ resolverFeedback }}</p>
            <p class="text-black font-bold dark:text-white">Name: {{ resolverName }}</p>
          </div>
        </article>
        <ul
          class="flex space-x-10 mt-10 mb-10"
          v-if="ticketStatus !== 'rejected' && ticketStatus !== 'resolved'"
        >
          <li
            class="w-10 h-10 rounded-lg p-1 cursor-pointer transition duration-200 text-blue-400 hover:bg-blue-100"
          >
            <svg
              @click="changeRoute"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M2.25 12.76c0 1.6 1.123 2.994 2.707 3.227 1.087.16 2.185.283 3.293.369V21l4.076-4.076a1.526 1.526 0 0 1 1.037-.443 48.282 48.282 0 0 0 5.68-.494c1.584-.233 2.707-1.626 2.707-3.228V6.741c0-1.602-1.123-2.995-2.707-3.228A48.394 48.394 0 0 0 12 3c-2.392 0-4.744.175-7.043.513C3.373 3.746 2.25 5.14 2.25 6.741v6.018Z"
              />
            </svg>

            <p class="mt-1 mb-1">Chat</p>
          </li>
          <li
            class="w-30 h-10 rounded-lg p-1 cursor-pointer transition duration-200 text-blue-400 hover:bg-blue-100"
          >
            <svg
              @click="toogle = !toogle"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-8"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M8.625 12a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0H8.25m4.125 0a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0H12m4.125 0a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0h-.375M21 12c0 4.556-4.03 8.25-9 8.25a9.764 9.764 0 0 1-2.555-.337A5.972 5.972 0 0 1 5.41 20.97a5.969 5.969 0 0 1-.474-.065 4.48 4.48 0 0 0 .978-2.025c.09-.457-.133-.901-.467-1.226C3.93 16.178 3 14.189 3 12c0-4.556 4.03-8.25 9-8.25s9 3.694 9 8.25Z"
              />
            </svg>

            <p class="mt-1 mb-1">Schedule Chat</p>
          </li>
        </ul>
        <div v-if="toogle">
          <input
            class="mt-8 mb-4 mr-2 outline-none rounded-lg dark:text-black-2 dark:placeholder:text-slate-600"
            type="text"
            v-model="chatDate"
            placeholder="Enter date and time ..."
          />
          <button
            v-if="!chatDateLoading"
            @click="submitDate"
            class="bg-blue-500 hover:bg-blue-800 text-white px-6 py-2 rounded-xl"
          >
            Schedule
          </button>
          <Loader v-if="chatDateLoading"></Loader>
        </div>
      </section>
      <section
        v-show="username && (ticketStatus === 'pending' || ticketStatus === 'processing')"
        class="mt-6 border rounded-xl bg-gray-50 mb-3"
      >
        <textarea
          class="w-full bg-gray-50 p-2 rounded-xl outline-none dark:text-black-2 dark:placeholder:text-slate-600"
          placeholder="Give your feedback here..."
          rows="3"
          v-model="feedback"
        ></textarea>
        <div class="flex items-center justify-between p-2">
          <button
            v-if="!feedbackLoader"
            @click="resolve"
            class="bg-blue-600 text-white px-6 py-2 rounded-xl hover:bg-blue-800"
          >
            Resolve
          </button>
          <Loader v-if="feedbackLoader"></Loader>
          <button
            v-if="!feedbackLoader"
            @click="rejected"
            class="bg-blue-600 hover:bg-blue-800 text-white px-6 py-2 rounded-xl"
          >
            Reject
          </button>
          <button
            v-if="!feedbackLoader && !(ticketStatus === 'processing')"
            @click="processing"
            class="bg-blue-600 hover:bg-blue-800 text-white px-6 py-2 rounded-xl"
          >
            Process
          </button>
        </div>
      </section>
    </section>
    <section
      v-else
      class="w-5/12 px-4 flex flex-col bg-white rounded-r-1xl overflow-y-auto dark:bg-black dark:text-white"
    ></section>
  </main>
  <transition name="fade">
    <Modal v-if="on" role="resolver" :friendId="userId" @toogle="ModalClose" />
  </transition>
</template>
<script setup>
import PageLoader from './PageLoader.vue'
import apiClient from '../../services/api.js'
import Modal from './Modal.vue'
import Loader from './Loader.vue'
import { onMounted, ref } from 'vue'
import { toast } from 'vue3-toastify'
import 'vue3-toastify/dist/index.css'
import { useAuthStore } from '../../store/auth.js'
import { useRoute, useRouter } from 'vue-router'
import { getCookie, deleteCookie } from '../../helper/CookieHelper.js'
import DarkModeSwitcher from '../Header/DarkModeSwitcher.vue'

const cards = ref([])
const route = useRoute()
const route1 = useRouter()
const { authenticated, toggleState } = useAuthStore()
const status = ref('')
const on = ref(false)
const toogle = ref(false)
const chatDate = ref('')
const chatDateLoading = ref('')
const logoutLoading = ref(false)
const feedback = ref('')
const ticketStatus = ref('')
const username = ref('')
const email = ref('')
const userId = ref('')
const title = ref('')
const body = ref('')
const ticketId = ref('')
const resolverName = ref(null)
const resolverFeedback = ref(null)
const profile = ref('http://[::1]:5173/storage/app/uploads/profile.png')
const loadingTickets = ref(true)
const feedbackLoader = ref(false)

toast.success('Welcome back', {
  autoClose: 1000
})
const ModalClose = () => {
  console.log('modal close')
  on.value = !on.value
}
const logoutHandler = () => {
  logoutLoading.value = true
  apiClient
    .get('/api/logout')
    .then((response) => {
      toggleState()

      deleteCookie('role')
      deleteCookie('resolverId')

      logoutLoading.value = false
      route1.push('/')
    })
    .catch((error) => {
      console.log(error)
      toast.error('Error occured,Please try again later', {
        autoClose: 1000
      })
      logoutLoading.value = false
    })
}
const submitDate = () => {
  chatDateLoading.value = true
  const resolverId = getCookie('resolverId')
  const payload = {
    timestamp: chatDate.value
  }
  chatDate.value = ''
  apiClient
    .post(`api/messages/${resolverId}/notify/${userId.value}`, payload)
    .then((response) => {
      console.log(response.data)
      toast.success('Invitation sent !', {
        autoClose: 1000
      })
      chatDateLoading.value = false
      // this.$emit('loadagain')
    })
    .catch((error) => {
      toast.error('Error occured,Please try again later', {
        autoClose: 1000
      })
      chatDateLoading.value = false
      console.log(error)
    })
}
const changeRoute = () => {
  // route1.push(`/chat?role=resolver&friendId=${userId.value}`)
  on.value = !on.value
  console.log(on.value)
}
const setAttributes = (item) => {
  console.log(item)
  title.value = item.data.attributes.title
  username.value = item.data.attributes.user.data.attributes.name
  email.value = item.data.attributes.user.data.attributes.email
  ticketId.value = item.data.ticket_id
  ticketStatus.value = item.data.attributes.status
  body.value = item.data.attributes.body
  userId.value = item.data.attributes.user.data.user_id

  if (item.data.attributes.user.data.attributes.img !== '') {
    profile.value = `http://[::1]:5173/storage/app/uploads/${item.data.attributes.user.data.attributes.img}`
  }
  console.log(ticketId.value)
}
onMounted(() => {
  if (!authenticated) {
    route1.push('/')
  } else {
    getResolvedTickets()
  }
})
const getResolvedTickets = () => {
  ticketStatus.value = ''
  loadingTickets.value = true
  apiClient
    .get(`/api/resolvers/${route.params.id}/tickets`)
    .then((response) => {
      cards.value = response.data.data.tickets.resolved
      username.value = cards.value[0].data.attributes.user.data.attributes.name
      email.value = cards.value[0].data.attributes.user.data.attributes.email
      ticketId.value = cards.value[0].data.ticket_id
      title.value = cards.value[0].data.attributes.title
      ticketStatus.value = cards.value[0].data.attributes.status
      body.value = cards.value[0].data.attributes.body
      userId.value = cards.value[0].data.attributes.user.data.user_id
      resolverName.value = cards.value[0].data.attributes.resolver
      resolverFeedback.value = cards.value[0].data.attributes.feedback

      if (cards.value[0].data.attributes.user.data.attributes.img !== '') {
        profile.value = `http://[::1]:5173/storage/app/uploads/${cards.value[0].data.attributes.user.data.attributes.img}`
      }
      console.log(response.data)
      loadingTickets.value = false
    })
    .catch((error) => {
      console.log(error)
      loadingTickets.value = false
    })
}

const getPendingTickets = () => {
  ticketStatus.value = ''
  loadingTickets.value = true
  apiClient
    .get(`/api/resolvers/${route.params.id}/tickets`)
    .then((response) => {
      cards.value = response.data.data.tickets.pending
      username.value = cards.value[0].data.attributes.user.data.attributes.name
      email.value = cards.value[0].data.attributes.user.data.attributes.email
      ticketId.value = cards.value[0].data.ticket_id
      title.value = cards.value[0].data.attributes.title
      ticketStatus.value = cards.value[0].data.attributes.status
      body.value = cards.value[0].data.attributes.body
      userId.value = cards.value[0].data.attributes.user.data.user_id
      if (cards.value[0].data.attributes.user.data.attributes.img !== '') {
        profile.value = `http://[::1]:5173/storage/app/uploads/${cards.value[0].data.attributes.user.data.attributes.img}`
      }
      console.log(cards.value)
      loadingTickets.value = false
    })
    .catch((error) => {
      console.log(error)
      loadingTickets.value = false
    })
}

const capitalizeFirstLetter = (str) => {
  // Check if the input string is not empty
  if (str.length === 0) {
    return str
  }

  // Capitalize the first letter and concatenate the rest of the string
  return str.charAt(0).toUpperCase() + str.slice(1)
}

const getRejectedTickets = () => {
  ticketStatus.value = ''
  loadingTickets.value = true
  apiClient
    .get(`/api/resolvers/${route.params.id}/tickets`)
    .then((response) => {
      cards.value = response.data.data.tickets.rejected
      username.value = cards.value[0].data.attributes.user.data.attributes.name
      email.value = cards.value[0].data.attributes.user.data.attributes.email
      ticketId.value = cards.value[0].data.ticket_id
      title.value = cards.value[0].data.attributes.title
      ticketStatus.value = cards.value[0].data.attributes.status
      body.value = cards.value[0].data.attributes.body
      userId.value = cards.value[0].data.attributes.user.data.user_id
      resolverName.value = cards.value[0].data.attributes.resolver
      resolverFeedback.value = cards.value[0].data.attributes.feedback
      if (cards.value[0].data.attributes.user.data.attributes.img !== '') {
        profile.value = `http://[::1]:5173/storage/app/uploads/${cards.value[0].data.attributes.user.data.attributes.img}`
      }
      console.log(cards.value)
      loadingTickets.value = false
    })
    .catch((error) => {
      console.log(error)
      loadingTickets.value = false
    })
}
const getProcessingTickets = () => {
  ticketStatus.value = ''
  loadingTickets.value = true
  apiClient
    .get(`/api/resolvers/${route.params.id}/tickets`)
    .then((response) => {
      cards.value = response.data.data.tickets.processing
      username.value = cards.value[0].data.attributes.user.data.attributes.name
      email.value = cards.value[0].data.attributes.user.data.attributes.email
      ticketId.value = cards.value[0].data.ticket_id
      title.value = cards.value[0].data.attributes.title
      ticketStatus.value = cards.value[0].data.attributes.status
      body.value = cards.value[0].data.attributes.body
      userId.value = cards.value[0].data.attributes.user.data.user_id
      resolverName.value = cards.value[0].data.attributes.resolver
      resolverFeedback.value = cards.value[0].data.attributes.feedback
      if (cards.value[0].data.attributes.user.data.attributes.img !== '') {
        profile.value = `http://[::1]:5173/storage/app/uploads/${cards.value[0].data.attributes.user.data.attributes.img}`
      }
      console.log(cards.value)
      loadingTickets.value = false
    })
    .catch((error) => {
      console.log(error)
      loadingTickets.value = false
    })
}
const resolve = () => {
  feedbackLoader.value = true
  status.value = 'resolved'
  const payload = {
    feedback: feedback.value,
    status: status.value
  }
  feedback.value = ''
  apiClient
    .put(`/api/resolvers/${route.params.id}/tickets/${ticketId.value}`, payload)
    .then((response) => {
      console.log(response.data)
      feedbackLoader.value = false
      toast.success('Successfully updated', {
        autoClose: 1000
      })
      getResolvedTickets()
      // this.$emit('loadagain')
    })
    .catch((error) => {
      feedbackLoader.value = false
      toast.error('Error occured,Please try again later', {
        autoClose: 1000
      })
      console.log(error)
    })
}
const rejected = () => {
  status.value = 'rejected'
  feedbackLoader.value = true
  // this.toggle = !this.toggle
  const payload = {
    feedback: feedback.value,
    status: status.value
  }
  feedback.value = ''
  apiClient
    .put(`/api/resolvers/${route.params.id}/tickets/${ticketId.value}`, payload)
    .then((response) => {
      console.log(response.data)
      toast.success('Successfully updated', {
        autoClose: 1000
      })
      feedbackLoader.value = false
      getRejectedTickets()
      // this.$emit('loadagain')
    })
    .catch((error) => {
      toast.error('Error occured,Please try again later', {
        autoClose: 1000
      })
      feedbackLoader.value = false
      console.log(error)
    })
}
const processing = () => {
  status.value = 'processing'
  feedbackLoader.value = true
  const payload = {
    feedback: feedback.value,
    status: status.value
  }
  feedback.value = ''
  // this.toggle = !this.toggle
  apiClient
    .put(`/api/resolvers/${route.params.id}/tickets/${ticketId.value}`, payload)
    .then((response) => {
      console.log(response.data)
      toast.success('Successfully updated', {
        autoClose: 1000
      })
      feedbackLoader.value = false
      getProcessingTickets()
      // this.$emit('loadagain')
    })
    .catch((error) => {
      toast.error('Error occured,Please try again later', {
        autoClose: 1000
      })
      feedbackLoader.value = false
      console.log(error)
    })
}
</script>
<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.section {
  /* Target the scrollbar track */
  height: 100vh;
  ::-webkit-scrollbar {
    width: 8px;
  }

  /* Track */
  ::-webkit-scrollbar-track {
    background: white;
  }

  /* Handle */
  ::-webkit-scrollbar-thumb {
    background: #888;
  }

  /* Handle on hover */
  ::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
}
</style>