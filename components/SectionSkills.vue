<template>
  <base-section
    id="portfolio"
    class="items-center justify-center"
    :title="$t('portfolio')"
  >
    <div class="flex flex-col">
      <base-card class="bg-secondary mx-4">
        <card-text class="flex" no-padding>
          <span
            class="mdi self-center md:self-auto mdi-code-tags text-8xl color-primary mr-2"
          />
          <div class="flex flex-col">
            <h2>Frontend</h2>
            <p>{{ $t("frontendDescription") }}</p>
            <chip-river :values="frontendTechnologies" class="mt-2" />
          </div>
        </card-text>
      </base-card>
      <base-card class="bg-secondary mx-4 mt-4 md:mt-8">
        <card-text class="flex" no-padding>
          <span
            class="mdi self-center md:self-auto mdi-server text-8xl color-primary mr-2"
          />
          <div class="flex flex-col">
            <h2>Backend</h2>
            <p>{{ $t("backendDescription") }}</p>
            <chip-river :values="backendTechnologies" class="mt-2" />
          </div>
        </card-text>
      </base-card>
      <base-card class="bg-secondary mx-4 mt-4 md:mt-8">
        <card-text class="flex" no-padding>
          <span
            class="mdi self-center md:self-auto mdi-database text-8xl color-primary mr-2"
          />
          <div class="flex flex-col">
            <h2>{{ $t("database") }}</h2>
            <p>{{ $t("databaseDescription") }}</p>
            <chip-river :values="databaseTechnologies" class="mt-2" />
          </div>
        </card-text>
      </base-card>
      <base-card class="bg-secondary mx-4 mt-4 md:mt-8">
        <card-text class="flex" no-padding>
          <span
            class="mdi self-center md:self-auto mdi-translate text-8xl color-primary mr-2"
          />
          <div class="flex flex-col">
            <h2>{{ $t("language") }}</h2>
            <p>{{ $t("languagesDescription") }}</p>
            <chip-river :values="languages" class="mt-2" />
          </div>
        </card-text>
      </base-card>
    </div>
  </base-section>
</template>

<script>
export default {
  name: 'SectionSkills',
  data () {
    return {
      frontendTechnologies: [
        'HTML5',
        'CSS3',
        'SCSS',
        'Tailwind CSS',
        'Bootstrap',
        'Vuetify',
        'Javascript',
        'Vue.js',
        'Angular',
        'Nuxt.js'
      ],
      backendTechnologies: [
        'Javascript',
        'PHP',
        'Node.js',
        'Express.js',
        'Laravel'
      ],
      databaseTechnologies: ['MariaDB', 'MySQL', 'PostgreSQL', 'MongoDB'],
      languages: ['English', 'Español']
    }
  }
}
</script>

<style>

</style>
