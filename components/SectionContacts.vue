<template>
  <base-section
    id="social-networks"
    class="items-center justify-center"
    :title="$t('contacts')"
    title-alignment="self-center"
  >
    <div class="flex text-7xl md:text-8xl">
      <a
        v-for="(link, index) in socialLinks"
        :key="link + index"
        :href="link.link"
        class="social-link"
      >
        <span :class="`mdi ${link.icon} color-primary`" />
      </a>
    </div>
    <base-card class="mt-8 p-4">
      <h2 class="text-base sm:text-2xl font-bold">
        {{ $t("formTitle") }}
      </h2>
      <app-alert v-if="message.active" :text="message.text" class="mt-3" :type="message.type" />
      <form
        id="form"
        name="contact"
        data-netlify="true"
        @submit.prevent="submitForm"
      >
        <div class="flex flex-col">
          <base-input-text
            v-model="form.name"
            :label="$t('form.name')"
            class="mt-3"
            required
            placeholder="John Doe"
            name="name"
          />
          <base-input-text
            v-model="form.address"
            :label="$t('form.email')"
            class="mt-3"
            type="email"
            required
            placeholder="john@mail.com"
            name="email"
          />
          <base-area-text
            v-model="form.body"
            :label="$t('form.message')"
            required
            placeholder="Lorem ipsum dolor sit amet consectetur adipisicing elit."
            class="mt-3"
            name="message"
          />
          <base-button class="mt-3 self-start" :loading="loading">
            {{ $t("button.send") }}
          </base-button>
        </div>
      </form>
    </base-card>
  </base-section>
</template>

<script>
export default {
  name: 'SectionContacts',
  data () {
    return {
      socialLinks: [
        {
          link: 'https://www.linkedin.com/in/jose-garcia-888941180/',
          icon: 'mdi-linkedin'
        },
        {
          link: 'https://stackoverflow.com/users/10824037/jogarcia',
          icon: 'mdi-stack-overflow'
        },
        {
          link: 'https://github.com/Tauromachian',
          icon: 'mdi-github'
        },
        {
          link: 'https://t.me/BetanKore',
          icon: 'mdi-telegram'
        },
        {
          link: 'https://www.reddit.com/user/BetanKore',
          icon: 'mdi-reddit'
        }
      ],
      form: {
        name: '',
        address: '',
        subject: 'Work for me',
        body: ''
      },
      message: { success: true, text: '', active: false },
      loading: false
    }
  },
  methods: {
    async submitForm () {
      this.loading = true
      const emailServiceToken = process.env.NUXT_ENV_EMAIL_SERVICE_TOKEN
      const recipientEmail = process.env.NUXT_ENV_RECIPIENT

      const body = {
        ...this.form,
        token: emailServiceToken,
        recipient: recipientEmail
      }

      let response
      try {
        response = await fetch(
          'https://jts-email-service.herokuapp.com/api/email-service',
          {
            method: 'POST',
            body: JSON.stringify(body),
            headers: {
              'Content-Type': 'application/json'
            }
          }
        )
      } catch (error) {
        this.displayErrorMessage()
        return
      }
      if (response.error) {
        this.displayErrorMessage()
        return
      }
      this.displaySuccessMessage()
      this.loading = false
    },
    displaySuccessMessage () {
      this.message.success = true
      this.message.text = 'Success! email sent correctly'
      this.message.active = true
      this.loading = false
    },
    displayErrorMessage () {
      this.message.success = false
      this.message.text = 'Error there was a problem sending the email'
      this.message.active = true
      this.loading = false
    }
  }
}
</script>

<style>

</style>
