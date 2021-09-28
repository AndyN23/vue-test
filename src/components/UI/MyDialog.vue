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
        date(){
            return{
                treeData:[],
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
            makeFolder: function(item) {
                Vue.set(item, "children", []);
                this.addItem(item);
            },
            addItem: function(item) {
                item.children.push({
                    name: "new folder"
                });
            },
            toggle: function() {
                if (this.isFolder) {
                this.isOpen = !this.isOpen;
                }
            },
            makeFolder: function() {
                if (!this.isFolder) {
                this.$emit("make-folder", this.item);
                this.isOpen = true;
                }
            }
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
        padding: 10px;
        display: flex;
        flex-direction: column;
    }

    &-close{
        background-color: #d42f2f;
        padding: 10px 10px;
        

        &:hover{
            background-color: #b62929;
        }
    }
}

// .button.add-folder{
//     font-size: 24px;
//     font-weight: bold;
//     width: 30px;
//     height: 30px;
//     background-color: #3153eb;
//     border: 1px solid #253bbb;
//     border-radius: 50%;
//     color:#fff;
//     display: flex;
//     justify-content: center;
//     align-items: center;
//     padding: 0;

//     &:hover{
//         background-color: #253bbb;
//     }
// }

</style>