<script>
import hljs from "highlight.js";

import "highlight.js/styles/github-dark.css";
var xhr = new XMLHttpRequest();
xhr.open("GET", "/src/data/data.json", false);
xhr.onload = function () {
    if (xhr.status === 200 && xhr.readyState === 4) {
        hljs.highlightAll();
    }
}
xhr.send();

const jsonOrg = JSON.parse(xhr.responseText);
var jsonData = JSON.parse(xhr.responseText);
export default {
    jsonData, jsonOrg
}
</script>