<template>
    <div class="license-filter row">
        <form @submit.prevent="applyFilters">
            <Input type="text" placeholder="Search" v-model="filters.search" class="col-md-6 col-sm-12 col-xs-12 search-box"/>
            <Input type="text" placeholder="Zipcode" v-model="filters.zip" class="col-md-2 col-sm-4 col-xs-4 zip-box"/>
            <Select placeholder="Type of License" :options="license.licenseTypes" v-model="filters.licenseType" class="col-md-3 col-sm-4 col-xs-4 type-select"/>
            <div class="col-md-1 col-sm-4 col-xs-4">
                <input type="submit" value="Search"/>
            </div>
        </form>
    </div>
</template>

<script>
    import Input from './../../components/input.vue';
    import Select from './../../components/select.vue';
    import Vuex from 'vuex/dist/vuex';

    export default {
        components: {
            Input,
            Select
        },
        data() {
            return {
                filters: {
                    search: "",
                    zip: "",
                    licenseType: ""
                }
            }
        },
        computed: {
            ...Vuex.mapState(['license'])
        },
        methods: {
            applyFilters() {
                this.$store.dispatch("applyFilter", this.filters);
            }
        }
    }
</script>