<script>
import axios from 'axios';
import ProjectCard from './ProjectCard.vue';
export default {
    name: 'SectionMain',
    data() {
        return {
            base_api_url: 'http://127.0.0.1:8000/',
            projects_endpoint: 'api/projects',
            projects: '',
        };
    },
    components: { ProjectCard },
    methods: {
        goTo(url) {
            console.log(url);
            this.callApi(url);
        },
        callApi(url) {
            axios
                .get(url)
                .then((resp) => {
                    //console.log(resp.data.results);
                    this.projects = resp.data.results;
                })
                .catch((error) => {
                    console.error(error);
                });
        }
    },
    mounted() {
        const url = this.base_api_url + this.projects_endpoint;
        this.callApi(url);
    }
}
</script>
<template>
    <main>
        <div class="p-5 mb-4 text-light">
            <div class="container py-5">
                <h1 class="fw-bold">Benvenuto nel Boolfolio di Andrea Parrini</h1>
                <p class="col-md-8 fs-4">
                    In questo sito potrai trovare tutti i progetti fatti da Andrea in tutto il suo percorso in boolean, in
                    ognuno
                    verranno indicate tutte le tecngologie utilizzate oltre alla categoria.
                </p>
                <button class="btn btn-primary btn-lg" type="button">
                    Example button
                </button>
            </div>
        </div>

        <div class="section-projects bg-light">
            <div class="container">
                <nav class="navbar navbar-expand-sm navbar-light bg-light">
                    <div class="container">
                        <div class="collapse navbar-collapse d-flex justify-content-between py-3" id="collapsibleNavId">
                            <h4 class="text-uppercase" href="#">All Projects</h4>
                            <form class="d-flex my-2 my-lg-0">
                                <input class="form-control me-sm-2" type="text" placeholder="Search" />
                                <button class="btn btn-outline-success my-2 my-sm-0" type="submit">
                                    Search
                                </button>
                            </form>
                        </div>
                    </div>
                </nav>
                <div class="row row-cols-3 ">
                    <div class="col my-2 " v-for="project in projects.data">
                        <ProjectCard :project="project" :base_api_url="this.base_api_url"></ProjectCard>
                    </div>
                </div>
                <nav aria-label="Page navigation " class="py-4">
                    <ul class="pagination">{{ console.log(projects.links) }}
                        <li v-for="link in     projects.links    " class="page-item"
                            :class="!(link.url) ? 'disabled' : '', link.active ? 'active' : ''">
                            <button class="page-link" :href="link.url" type="button" @click="goTo(link.url)">
                                <span v-html="link.label"></span>
                            </button>
                        </li>
                    </ul>
                </nav>

            </div>
        </div>
    </main>
</template>


<style lang="scss" scoped></style>