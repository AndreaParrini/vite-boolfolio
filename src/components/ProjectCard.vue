<script>
export default {
    name: 'ProjectCard',
    props: {
        project: Object,
        base_api_url: String
    }
}
</script>
<template>
    <div class="card h-100">
        <img v-if="project.cover_image" height="400"
            :src="project.cover_image.startsWith('https://') ? project.cover_image : this.base_api_url + 'storage/' + project.cover_image"
            class="card-img-top ratio" alt="...">
        <div class="card-body">
            <h5 class="card-title text-uppercase">{{ project.title }}</h5>
            <div class="card-subtitle mb-2 text-muted " v-if="project.technologies.length > 0">
                <span class="badge bg-primary mx-1" v-for="tec in project.technologies">{{ tec.name
                }}</span>

            </div>
            <div class="card-subtitle mb-2 text-muted " v-else> Non ci sono tecnologie in questo
                progetto</div>

            <p class="card-text">S{{ project.content }}</p>
        </div>
    </div>
</template>


<style lang="scss" scoped></style>