<template>
    <div id="app">

        <Viewer :markdown="'hello'" />

    </div>
</template>

<script>
export default Vue.defineComponent({
    name: 'App',
    components: {
        "Viewer": Vue.defineAsyncComponent(() => loadModule("Viewer.vue", options))
    },
    setup() {
        //set up i18n
        const { t } = VueI18n.useI18n()
        return { t }
    },
})
</script>