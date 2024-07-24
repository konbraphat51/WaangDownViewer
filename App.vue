<template>
    <div id="app">

        <Viewer :markdown="'hello'" />

    </div>
</template>

<script>
export default Vue.defineComponent({
    name: 'App',
    data() {
        return {
            markdown: `
            # h1
            aaaaaaa
            あああああああああああ

            あああああああああ

            ## h2
            aaaaaaaaaaaaaaaaaa
            ああああああああああああああああああ

            ### h3
            aaaaaaaaaaaaaaaaaaaaa
            あああああああああああああああああああ

            #### h4
            aaaaaaaaaaaaaaaaaaaaa
            ああああああああああああああああ

            ##### h5
            aaaaaaaaaaaaaaaaaaaa
            あああああああああああああああ

            ###### h6
            aaaaaaaaaaaaaaaaaaaaa
            あああああああああああああああああ

            - list1
            - list2
            - list3

            1. list1
            2. list2
            3. list3

            [link](https://www.google.com)
            
            image
            
            ![image](https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png)

            **bold**
            *italic*
            ***bold italic***

            **太字**
            *斜体*
            ***太字 斜体***

            > quote

            \`code\`
            `
        }
    },
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