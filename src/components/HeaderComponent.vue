<template>
    <div>
        <div class="dashboard-header">
            <nav class="navbar navbar-expand-lg bg-white fixed-top">
                <a class="navbar-brand">Concept</a>
                <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse " id="navbarSupportedContent">
                    <ul class="navbar-nav ml-auto navbar-right-top">
                        <li class="nav-item">
                            <div id="custom-search" class="top-search-bar">
                                <input class="form-control" type="text" placeholder="Search..">
                            </div>
                        </li>
                    </ul>
                    <select @change="handleChangeLocale($event)">
                        <option v-for="(locale, index) in locales" v-bind:key="index" :value="locale">{{ $t(`locales.${locale}`) }}</option>
                    </select>
                </div>
            </nav>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            locales : [],
        }
    },
    mounted() {
        this.getLocales()
    },
    methods : {
        getLocales() {
            for (const key in this.$i18n.messages) {
                this.locales.push(key)
            }
        },
        handleChangeLocale(event) {
            this.$i18n.locale = event.target.value
            localStorage.setItem('lang', event.target.value)
        }
    }
}
</script>

<style>
</style>
