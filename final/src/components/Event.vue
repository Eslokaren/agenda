<template>
       
         <tr>
          <td>{{name}}</td>
          <td>{{phone}}</td>
          <td>{{email}}</td>
          <td>{{location}}</td>
          <td><mdb-badge @click.native="onDelete" tag="a"><mdb-icon icon="trash-alt" class="text-danger " /></mdb-badge><mdb-badge @click.native="modal = true" tag="a"  class="mx-5" ><mdb-icon icon="user-edit" color="default"/></mdb-badge></td>
        </tr>

</template>
<script>
import { mdbBadge, mdbIcon, mdbTblBody,mdbDatatable } from "mdbvue";

export default {
  name: "Event",
  components: {
    mdbBadge,
    mdbIcon,
    mdbTblBody
  },
  props: {
    index: {
      type: Number
    },
    name: {
      type: String
    },
    phone: {
      type: String
    },
    location: {
      type: String
    },
    email: {
      type: String
    },
    modal:{
      type:Boolean
    }
  },
   computed: {
        modallocal: {
            get: function() {
                return this.modal
            },
            set: function(value) {
                this.$emit('update:modal', JSON.parse(this.modal).value)
            }
        }
    },
  methods: {
    onDelete() {
      this.$emit("delete", this.index);
    }
  }
};
</script>


