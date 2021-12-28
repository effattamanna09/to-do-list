<template>
    <div class="item">
<input type="checkbox"
@change="updateCheck()"
v-model="item.completed"/>
<span :class="[item.completed ? 'completed' : '', 'itemText']">{{item.name}}</span>
       <button @click="removeItem()" class="trashcan"></button>
        <font-awesome-icon icon="trash" />
        </div>
</template>

<script>
export default {
    props: ['item'],
    methods: {
        updateCheck() {
            axios.put('api/item' + this.item.id,{
                item: this.item
            })
            .this(response => {
                if( response.status == 200){
                    this.$emit('itemchanged');
                }
            })
            .catch( error =>{
                console.log( error );
            })
        },
        removeItem() {
            axios.delete('api/item' + this.item.id)
            .then(response => {
                if(response.status == 200){
                    this.$emit('itemchanged');
                }
            })
            .catch(error => {
                console.log(error);
            })
        }
    }

}
</script>


<style scoped>
.completed {
    text-decoration: line-through;
    color: cornsilk;
}

.itemText{
    width: 100%;
    margin-left: 20px;
}


.trashcan{
    background: darkgray;
    border: none;
    color: crimson;
    outline: none;
}

</style>