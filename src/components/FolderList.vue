<template>
    <div class="folder-list">
        <h2 class="">My Folders Tree</h2>
        <ol id="demo">
            <list-item
                class="item"
                :item="treeData"
                @make-folder="makeFolder"
                @add-item="addItem"
            ></list-item>
        </ol>
    </div>
</template>

<script>
import MyFolder from "@/components/MyFolder";
    export default {
        components: {MyFolder},
        name: 'folder-list',
        data() {
            return{
                treeData: {
                    children: [
                        { name: "Folder" },
                        { name: "Folder2" },
                        {
                            name: "child folder",
                            children: [
                                {
                                    name: "child folder",
                                    children: [{ name: "Folder" }, { name: "Folder2" }]
                                },
                                { name: "Folder" },
                                { name: "Folder2" },
                                {
                                    name: "child folder",
                                    children: [{ name: "Folder" }, { name: "Folder2" }]
                                }
                            ]
                        }
                    ]
                }
            }
        },
        methods: {
            makeFolder: function(item) {
                Vue.set(item, "children", []);
                this.addItem(item);
            },
            addItem: function(item) {
                item.children.push({
                    name: "new folder"
                });
            }
        }
    }
</script>

<style lang="scss" scoped>

    .folder-list{
        margin: 10px;
    }

    ol, li{
        padding-left: 1em;
        line-height: 1.5em;
        list-style-type: dot;
    }


</style>