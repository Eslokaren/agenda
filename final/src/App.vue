<template>
  <mdb-container>
    <!-- Navbar-->
    <mdb-navbar expand="large" light class="juicy-peach-gradient mb-4">
    <mdb-navbar-brand href="#">
     <mdb-icon icon="pencil-alt" />    MyContacts
    </mdb-navbar-brand>
    <mdb-navbar-toggler>
      <mdb-navbar-nav right> 
        <form >
        <mdb-input type="text" class="text-white" placeholder="Search" aria-label="Search"  v-moldel="name"/>
      </form>                
      </mdb-navbar-nav>
    </mdb-navbar-toggler>
  </mdb-navbar>
   <!--muestra de los contactos -->
    <mdb-row>
      <mdb-col col="12">
        <h2 class="text-uppercase my-3 ">Contacts List:</h2>  
         <div>
        
          <mdb-tbl hover btn responsive  class="mb-5">
            <mdb-tbl-head class="cloudy-knoxville-gradient">
              <tr>
                <th><mdb-icon icon="user" color="default" />-----Name</th>
                <th><mdb-icon icon="mobile" color="default" />-----Phone Number</th>
                <th><mdb-icon icon="envelope"  color="default" />-----Email Address</th>
                <th><mdb-icon icon="map" color="default" />-----Location</th>
                <th></th>
              </tr>
            </mdb-tbl-head>
            <mdb-tbl-body>
          <Event
            v-for="(event, index) in events"
            :index="index"
            :name="event.name"
            :phone="event.phone"
            :email="event.email"
            :location="event.location"
            :modal="event. modallocal"
            :key="index"
            @delete="handleDelete"
            
          />
          </mdb-tbl-body>

          </mdb-tbl>  
      </div>  
        <mdb-row>
          <mdb-col  class=" text-center ">
            <mdb-btn  @click.native="modal = true" class="juicy-peach-gradient rounded-circle py-4 fixed-bottom float-right text-dark "><mdb-icon icon="user-plus" class="text-dark "/></mdb-btn>
          </mdb-col>
        </mdb-row>
      </mdb-col>
    </mdb-row>
   <!--La venta modalAdd-->
    <mdb-modal v-if="modal" @close="modal = false"  cascade class="text-left " >
      <mdb-modal-header  class="juicy-peach-gradient black-text">
        <h4 class="title"><fa class="fas fa-pencil-alt" /> MyContacts</h4>
      </mdb-modal-header>
      <mdb-modal-body class="grey-text">
        <form class="mx-3 grey-text">
          <mdb-input size="sm"
            name="name"
            label="name"
            icon="user"
            placeholder="name"
            type="text"
             validate error="wrong" primary="right"
            @input="handleInput($event, 'name')"
          />
          <mdb-input size="sm"
            name="email"
            label="email"
            icon="envelope"
            placeholder="email"
            type="text"
             validate error="wrong" success="right"
            @input="handleInput($event, 'email')"
          />
          <mdb-input size="sm"
            name="phone"
            label="phone"
            icon="mobile" 
            placeholder="phone"
            type="tel"
             validate error="wrong" success="right"
            @input="handleInput($event, 'phone')"
          />
           <mdb-input size="sm"
            name="location"
            label="location"
            icon="map"
            placeholder="location"
            type="text"
             validate error="wrong" success="right"
            @input="handleInput($event, 'location')"
          />
        </form>
      </mdb-modal-body>
      <mdb-modal-footer>
        <mdb-btn   @click.native="addEvent" class="juicy-peach-gradient rounded-circle py-4 fixed-bottom float-right text-dark "><mdb-icon far icon="paper-plane" class="text-dark "/></mdb-btn>
      </mdb-modal-footer>
    </mdb-modal>    
  </mdb-container>
</template>

<script>
import {
  mdbContainer,
  mdbRow,
  mdbCol,
  mdbIcon,
  mdbBtn,
  mdbModal,
  mdbModalHeader,
  mdbModalTitle,
  mdbModalBody,
  mdbModalFooter,
  mdbInput,
  mdbTextarea,
  mdbNavbar,
  mdbNavbarBrand,
  mdbNavbarToggler,
  mdbNavbarNav,
  mdbNavItem,
  mdbTbl,
  mdbTblHead,
  mdbDatatable ,
  mdbTblBody  
} from "mdbvue";
import Event from "@/components/Event";
export default {
  name: "App",
  components: {
  mdbContainer,
  mdbRow,
  mdbCol,
  mdbIcon,
  mdbBtn,
  mdbModal,
  mdbModalHeader,
  mdbModalTitle,
  mdbModalBody,
  mdbModalFooter,
  mdbInput,
  mdbTextarea,
  mdbNavbar,
  mdbNavbarBrand,
  mdbNavbarToggler,
  mdbNavbarNav,
  mdbNavItem,
  mdbTbl,
  mdbTblHead,
  mdbTblBody,
  mdbDatatable ,
  Event
  },
  data() {
    return {
      events: [
        {
          name: "Eslokaren",
          phone: "809-896-0580",
          location: "Azua,Republica Dominicana",
          email: "eslokaren@gmail.com"
        },
        {
          name: "Eslovenia",
          phone: "489-551-9670",
          location: "Barahona,Republica Dominicana",
          email: "eslovenia@gmail.com"
        },
        {
           name: "Maria",
          phone: "809-521-0580",
          location: "Puerto Plata,Republica Dominicana ",
          email: "maria@gmail.com"
        },
        {
          name: "Alenni",
          phone: "809-965-3280",
          location: "Bani,Republica Dominicana",
          email: "alenni@gmail.com"
        }
      ],
      modal: false,
      newValues: []
    };
  },
  methods: {
    handleDelete(eventIndex) {
      this.events.splice(eventIndex, 1);
    },
    handleInput(val, type) {
      this.newValues[type] = val;
    },
    addEvent() {
      this.events.push({
        name: this.newValues["name"],
        phone: this.newValues["phone"],
        location: this.newValues["location"],
        email: this.newValues["email"]
      });
    }
  }
};
</script>

<style>

</style>