<template>
    <div class="dialog" v-if="show" @click="hideDialog">
        <div class="dialog__content" @click.stop>
            <folder-list
            :item="treeData"
            @make-folder="makeFolder"
            @add-item="addItem"
            >
            </folder-list>
            <my-button @click="hideDialog" class="dialog-close" > X  Закрыть</my-button>
        </div>
    </div>
</template>

<script>
import  FolderList from '@/components/FolderList';
import  MyFolder from '@/components/MyFolder';
    export default {
        components: {FolderList, MyFolder},
        name: 'my-dialog', 
        data(){
            return{
                treeData: ['treeData']
            }
        },
        props: {
            show: {
                type: Boolean,
                default: false
            }
        },
        methods: {
            hideDialog() {
                this.$emit('update:show', false)
            },
            addItem: function(item) {
                item.children.push({
                    name: "new folder"
                });
            },
            makeFolder: function(item) {
                this.children.set(item, "children", []);
                this.addItem(item);
            },
        }
    }
</script>

<style lang="scss" scoped>

.dialog {
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: rgba($color: #000, $alpha: .5);
    position: fixed;
    display: flex;

    &__content {
        margin: auto;
        background-color: white;
        border-radius: 8px;
        min-height: 450px;
        min-width: 650px;
        padding: 10px 10px 25px;
        display: flex;
        flex-direction: column;
        box-sizing: border-box;
        justify-content: space-between;
    }

    &-close{
        background-color: #d42f2f;
        padding: 10px 10px;
        width: 50%;
        margin: 0 auto;
        

        &:hover{
            background-color: #b62929;
        }
    }
}

</style>