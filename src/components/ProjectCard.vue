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
    <!-- Modal trigger button -->
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
            <!-- Modal trigger button -->
            <button type="button" class="btn btn-primary btn-lg" data-bs-toggle="modal"
                :data-bs-target="`#modalId-${project.id}`">
                View
            </button>

            <!-- Modal Body -->
            <!-- if you want to close by clicking outside the modal, delete the last endpoint:data-bs-backdrop and data-bs-keyboard -->
            <div class="modal fade" :id="`modalId-${project.id}`" tabindex="-1" data-bs-backdrop="static"
                data-bs-keyboard="false" role="dialog" :aria-labelledby="`modalTitleId-${project.id}`" aria-hidden="true">
                <div class="modal-dialog modal-dialog-scrollable modal-dialog-centered modal-xl" role="document">
                    <div class="modal-content">
                        <div class="modal-header">
                            <h5 class="modal-title" :id="`modalTitleId-${project.id}`">
                                {{ project.title }}
                            </h5>
                            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                        </div>
                        <div><img v-if="project.cover_image" height="400"
                                :src="project.cover_image.startsWith('https://') ? project.cover_image : this.base_api_url + 'storage/' + project.cover_image"
                                class="card-img-top ratio" alt="..."></div>
                        <div class="modal-body">{{ project.content }}</div>
                        <div class="modal-footer">
                            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">
                                Close
                            </button>
                            <button type="button" class="btn btn-primary">Save</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<style lang="scss" scoped></style>