<template>
  <div>
    <h1>Jobs</h1>
    <ul>
      <li v-for="job in jobs" :key="job.id">
        {{ job.title }}
        <div>
          <div v-html="job.answer1"></div>
          <div v-html="job.answer2"></div>
          <div v-html="job.answer3"></div>
          <p>Type de contrat : {{ job.type }}</p>
          <p>Contact :{{ job.contactEmail }}</p>
          <p>Publié le : {{ job.submittedAt }}</p>
          <br>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      jobs: []
    };
  },
  async fetch() {
    try{
      const response = await fetch('https://app.staging.profilpublic.fr/api/jobs')
        .then(res => res.json())
        this.jobs = response.data
        // console.log(this.jobs)
    } catch (err){
      console.error('Erreur dans la récupération des données', err);
    }
  }
}

</script>
