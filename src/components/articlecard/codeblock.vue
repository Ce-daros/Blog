


<script>
import { PrismEditor } from "vue-prism-editor";

import "vue-prism-editor/dist/prismeditor.min.css";
import { highlight, languages } from "prismjs/components/prism-core";
import "prismjs/components/prism-clike";
import "prismjs/components/prism-javascript";
import "prismjs/themes/prism-tomorrow.css";

export default {
    components: {
        PrismEditor
    },
    props: ['c'],
    methods: {
        highlighter(code) {
            return highlight(this.c, languages.js); //returns html
        }
    }
};
</script>
<template>
    <prism-editor class="my-editor height-300" aria-disabled :highlight="highlighter" line-numbers :readonly="false"
        :tabSize="4"></prism-editor>
</template>
<style lang="scss">
.my-editor {
    background: var(--theme-dark);
    color: var(--theme-light);
    font-family: Fira code, Fira Mono, Consolas, Menlo, Courier, monospace;
    font-size: 14px;
    line-height: 1.5;
    border-radius: 15px;
    padding: 5px;
}

.prism-editor__textarea:focus {
    outline: none;
}

/* 非必须 */
.height-300 {
    height: 300px;
}
</style>