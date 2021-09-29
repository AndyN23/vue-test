<template>
    <div class="folder-list">
        <h2 class="folder-list__title">My Folders Tree</h2>
        <ul id="demo" class="folder__list">
            <list-item
                class="item"
                :item="treeData"
                @add-item="addItem"
                @dblclick="makeFolder"
            >

            </list-item>
        </ul>
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
                    name: 'Folder',
                    children: [
                        { name: "Folder" },
                        { name: "child folder",
                            children: [
                                {name: "child folder",
                                children: [{ name: "Folder" }, { name: "Folder2" }]
                                },
                                { name: "Folder" },
                                {name: "child folder",
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
                this.children.set(item, "children", []);
                this.addItem(item);
            },
            // makeFolder: function() {
            //     if (!this.isFolder) {
            //     this.$emit("make-folder", this.item);
            //     this.isOpen = true;
            //     }
            // },

            addItem: function(item) {
                item.children.push({
                name: "new folder"
                });
            },
            
        }
    }
</script>

<style lang="scss" scoped>

    .folder-list{
        margin: 15px;

        &__title{
            margin-bottom: 20px;
        }
    }

    .folder__list{
        display: flex;
        margin-left: 50px;
    }

</style>