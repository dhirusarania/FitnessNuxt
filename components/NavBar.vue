<template>
  <div>
    <div class="navbar-spacing padding-top-20">
      <nav class="topnav box-shadow padding-left-10 padding-right-10 row">
        <div class="flex align-item col" style="height:100%">
          <div class="visible-xs visible-sm">
            <a @click="toggleSidenav">
              <i data-feather="menu"></i>
            </a>
          </div>
          <div class="hidden-xs">
            <div class="tooltip_custom">
              <nuxt-link to="/dashboard/parcels/pending">
                <i data-feather="package"></i>
              </nuxt-link>
              <span class="tooltiptext">All Products</span>
            </div>
          </div>
        </div>

        <div
          class="flex align-item col right"
          style="height:100%; justify-content:flex-end"
        >
          <!-- <div style="position:relative;margin-right:15px">
          <span class="feather-icon-badge bg-primary text-white h-5 w-5 absolute rounded-full text-xs flex items-center justify-center" style="top: 5px; right: 0px;position:absolute;border-radius:50px;width:20px;height:20px">5</span>
          <nuxt-link to="/dashboard/general/messages">
            <i data-feather="message-square"></i>
          </nuxt-link>
          </div>-->
          <div class="flex align-item">
            <div style="padding-right:10px" class="hidden-xs">
              <p class="font-30">{{ currentUserEmail }}</p>
            </div>
          </div>
        </div>
      </nav>
    </div>

    <perfect-scrollbar
      id="mySidenav"
      class="sidenav hidden-xs hidden-sm padding-bottom-30"
    >
      <div class="flex align-item">
        <img src="" class="sideNav__Logo" />
        <div style="cursor:pointer" class="hidden-lg" @click="toggleSidenav">
          <i data-feather="x"></i>
        </div>
      </div>
      <p>Products</p>
      <div class="navbar__parent">
        <nuxt-link to="/products/new">
          <i data-feather="plus-square"></i>
          <span>New</span>
        </nuxt-link>
      </div>
      <div class="navbar__parent">
        <nuxt-link to="/products/all">
          <i data-feather="package"></i>
          <span>All</span>
        </nuxt-link>
      </div>
      <p>Orders</p>
      <div class="navbar__parent">
        <nuxt-link to="/orders/all">
          <i data-feather="plus-square"></i>
          <span>All</span>
        </nuxt-link>
      </div>
      <div class="navbar__parent">
        <nuxt-link to="/orders/pending">
          <i data-feather="package"></i>
          <span>Pending</span>
        </nuxt-link>
      </div>
      <p>Auction</p>
      <div class="navbar__parent">
        <nuxt-link to="/auction/new">
          <i data-feather="plus-square"></i>
          <span>Start Auction</span>
        </nuxt-link>
      </div>
      <div class="navbar__parent">
        <nuxt-link to="/auction/completed">
          <i data-feather="plus-square"></i>
          <span>Completed</span>
        </nuxt-link>
      </div>
      <div class="navbar__parent">
        <nuxt-link to="/auction/ongoing">
          <i data-feather="package"></i>
          <span>Ongoing</span>
        </nuxt-link>
      </div>
    </perfect-scrollbar>
  </div>
</template>


<script>
  // import feather from 'feather-icons'

  export default {
    data: () => ({
      active: false,
      currentUserEmail: '',
      pickup_count: 0,
      message_count: 0
    }),

    computed: {
      // active : $store.state.sidenavStatus
    },

    mounted() {
      feather.replace({ color: 'white' })

      this.currentUserEmail = localStorage.getItem('currentUserEmail')
    },
    methods: {
      toggleSidenav: function() {
        $('#mySidenav').toggleClass('hidden-xs hidden-sm')
      },
      logout: function() {
        document.cookie.split(';').forEach(function(c) {
          document.cookie = c
            .replace(/^ +/, '')
            .replace(/=.*/, '=;expires=' + new Date().toUTCString() + ';path=/')
        })

        this.$router.push('/')
      }
    }
  }
</script>

<style scoped>
.navbar__parent {
  padding: 0 15px;
}

.sideNav__Logo {
  width: 85%;
  object-fit: contain;
  height: 80px;
}

p {
  margin: 0;
}

.sidenav {
  height: 100%;
  width: 260px;
  position: fixed;
  z-index: 950;
  top: 0;
  left: 0;
  background-color: #0d164b;
  transition: all 0.5s;
  padding-top: 10px;
  box-shadow: 0 4px 20px 0 rgba(0, 0, 0, 0.5);
  overflow: auto;
}

.sidenav p {
  padding: 32px 8px 17px 30px;
  text-decoration: none;
  font-size: 14px;
  color: #ffffff;
  display: block;
  transition: 0.3s;
}

.sidenav a {
  padding: 10px 15px 10px 15px;
  text-decoration: none;
  font-size: 13px;
  color: rgb(194, 205, 220);
  display: block;
  transition: 0.3s;
  width: 100%;
  display: flex;
  align-items: center;
}

.sidenav span {
  padding-left: 10px;
}

.sidenav a:hover {
  color: rgb(115, 103, 240);
}

.sidenav .closebtn {
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 36px;
  margin-left: 50px;
}

@media screen and (max-height: 450px) {
  .sidenav {
    padding-top: 15px;
  }
  .sidenav a {
    font-size: 18px;
  }
}

.breadcrumb {
  background-color: #2c3350;
}

p {
  margin: 0;
}

.topnav {
  height: 62px;
  background-color: #10163a;
  border-radius: 7px;
}

.topnav a {
  float: left;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 10px;
  text-decoration: none;
  font-size: 17px;
}

.topnav a:hover {
  color: red;
}

.topnav a.active {
  background-color: #4caf50;
  color: white;
}

.notification {
  background-color: #ff9800;
  border-radius: 50%;
  height: 20px;
  width: 20px;
  margin-left: 10px;
  text-align: center;
  padding: 0 !important;
  font-size: 12px;
  color: white;
  line-height: 20px;
  font-weight: bold;
}

svg {
  width: 20px;
}
</style>

