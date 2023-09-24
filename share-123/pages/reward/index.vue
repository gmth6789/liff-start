<template>
  <div>
    <v-app-bar
      color="primary"
      dense
      flat
      dark
    >
    <v-toolbar-title>Reward Card</v-toolbar-title>
    </v-app-bar>
    <v-container class="pt-0 pb-0">
      <v-row>
        <v-col>
          <v-card class="mt-8">
            <v-card-text>
              <div class="d-flex">
                <div>
                  <img :src="getLine.pictureUrl" alt="" width="40" style="border-radius: 50%;">
                </div>
                <div class="align-self-center">
                  <h2 class="name text-primary m-0">{{ getUser.firstname }}</h2>
                </div>
              </div>
            </v-card-text>
            <div class="stamp-zone">
              <div class="stamp" v-for="(obj, index) in stamps" :key="index">
                <div class="circle" :class="obj.value == true ? 'active' : ''" v-if="index != Object.keys(stamps).length - 1">
                  <span>{{ index+1 }}</span>
                  <v-icon>check</v-icon>
                </div>
                <div class="circle end" :class="obj.value == true ? 'active' : ''" v-else>
                  <span>GOAL</span>
                  <v-icon>check</v-icon>
                </div>
              </div>              
            </div>
          </v-card>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <v-btn v-if="isDone == false" rounded color="primary" dark class="w-100 mt-10 my-btn scan" @click="scan">
            <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" id="fi_1490853" x="0px" y="0px" viewBox="0 0 490 490" style="enable-background:new 0 0 490 490;" xml:space="preserve" width="28" height="28"><g><g><path style="fill:#F0CD00;" d="M490,245c0,135.31-109.69,245-245,245c-71.33,0-135.54-30.48-180.31-79.13    c-11.76-12.77-22.17-26.8-31.03-41.85C12.27,332.64,0,290.25,0,245C0,109.69,109.69,0,245,0c45.26,0,87.65,12.27,124.02,33.67    c15.05,8.85,29.07,19.26,41.84,31.03C459.51,109.45,490,173.67,490,245z"></path><path style="fill:#FFDE50;" d="M490,245c0,132.26-104.79,240.04-235.88,244.83C123.03,485.04,18.24,377.26,18.24,245    S123.03,4.96,254.12,0.17C385.21,4.96,490,112.74,490,245z"></path><path style="fill:#FFEA94;" d="M410.86,64.7L64.69,410.87c-11.76-12.77-22.17-26.8-31.03-41.85L369.02,33.67    C384.07,42.52,398.09,52.93,410.86,64.7z"></path><path style="fill:#FFEA94;" d="M473.1,155.43L155.42,473.11c-22.49-8.84-43.36-20.91-62.03-35.64L437.47,93.39    C452.2,112.06,464.27,132.93,473.1,155.43z"></path><path style="fill:#FAA300;" d="M435.38,245c0,105.14-85.24,190.38-190.38,190.38c-36.62,0-70.82-10.34-99.85-28.26    c-12.65-7.8-24.31-17.05-34.77-27.51c-7.69-7.68-14.73-16.03-21.02-24.94c-8.66-12.27-15.91-25.61-21.5-39.78    c-8.28-20.95-12.94-43.73-13.22-67.55c-0.02-0.78-0.02-1.56-0.02-2.34c0-105.14,85.23-190.38,190.38-190.38    c0.78,0,1.57,0,2.35,0.02c23.82,0.28,46.59,4.95,67.54,13.22c14.17,5.6,27.51,12.84,39.78,21.5c8.91,6.3,17.25,13.33,24.94,21.02    c10.46,10.45,19.71,22.12,27.51,34.77C425.04,174.18,435.38,208.38,435.38,245z"></path><path style="fill:#FFBD00;" d="M379.61,110.38L110.38,379.61c-7.69-7.68-14.73-16.03-21.02-24.94    c-8.66-12.27-15.91-25.61-21.5-39.78c-8.28-20.95-12.94-43.73-13.22-67.55c-0.02-0.78-0.02-1.56-0.02-2.34    c0-105.14,85.23-190.38,190.38-190.38c0.78,0,1.57,0,2.35,0.02c23.82,0.28,46.59,4.95,67.54,13.22    c14.17,5.6,27.51,12.84,39.78,21.5C363.58,95.66,371.92,102.69,379.61,110.38z"></path><path style="fill:#F68E00;" d="M435.375,245c0,105.14-85.24,190.38-190.38,190.38c-3.61,0-7.19-0.1-10.75-0.3    c100.14-5.57,179.62-88.55,179.62-190.08s-79.48-184.51-179.62-190.08c3.56-0.2,7.14-0.3,10.75-0.3    C350.135,54.62,435.375,139.86,435.375,245z"></path></g><path style="fill:#F68E00;" d="M238.728,230.371V153.27c12.016,6.629,20.176,19.423,20.176,34.09   c0,10.346,8.387,18.733,18.733,18.733s18.733-8.387,18.733-18.733c0-35.651-24.557-65.669-57.642-74.043V98.069   c0-10.346-8.387-18.733-18.733-18.733s-18.733,8.387-18.733,18.733v15.247c-33.085,8.375-57.642,38.392-57.642,74.043   c0,21.287,6.252,37.887,19.113,50.748c9.377,9.377,21.833,16.316,38.529,21.403v77.222c-12.016-6.629-20.176-19.422-20.176-34.089   c0-10.346-8.387-18.733-18.733-18.733c-10.346,0-18.733,8.387-18.733,18.733c0,35.651,24.557,65.668,57.642,74.043v15.247   c0,10.346,8.387,18.733,18.733,18.733s18.733-8.387,18.733-18.733v-15.247c33.085-8.375,57.642-38.391,57.642-74.043   c0-20.992-6.52-38.155-19.378-51.013C267.647,242.284,255.036,235.278,238.728,230.371z M189.226,211.615   c-3.79-3.789-8.139-9.971-8.139-24.256c0-14.667,8.16-27.46,20.176-34.09v66.316C196.21,217.245,192.21,214.6,189.226,211.615z    M238.728,336.732v-66.521c16.281,7.582,20.176,18.429,20.176,32.432C258.904,317.31,250.744,330.103,238.728,336.732z"></path><path style="fill:#FFEA94;" d="M263.73,230.371V153.27c12.016,6.629,20.176,19.423,20.176,34.09   c0,10.346,8.387,18.733,18.733,18.733s18.733-8.387,18.733-18.733c0-35.651-24.557-65.669-57.642-74.043V98.069   c0-10.346-8.387-18.733-18.733-18.733s-18.733,8.387-18.733,18.733v15.247c-33.085,8.375-57.642,38.392-57.642,74.043   c0,21.287,6.252,37.887,19.113,50.748c9.377,9.377,21.833,16.316,38.529,21.403v77.222c-12.016-6.629-20.176-19.422-20.176-34.089   c0-10.346-8.387-18.733-18.733-18.733s-18.733,8.387-18.733,18.733c0,35.651,24.557,65.668,57.642,74.043v15.247   c0,10.346,8.387,18.733,18.733,18.733s18.733-8.387,18.733-18.733v-15.247c33.085-8.375,57.642-38.391,57.642-74.043   c0-20.992-6.52-38.155-19.378-51.013C292.649,242.284,280.037,235.278,263.73,230.371z M214.227,211.615   c-3.79-3.789-8.139-9.971-8.139-24.256c0-14.667,8.16-27.46,20.176-34.09v66.316C221.212,217.245,217.212,214.6,214.227,211.615z    M263.73,336.732v-66.521c16.281,7.582,20.176,18.429,20.176,32.432C283.905,317.31,275.746,330.103,263.73,336.732z"></path></g></svg>
            แชร์เพื่อรับรางวัล
          </v-btn>
          <v-btn v-if="isDone == true" rounded color="primary" dark class="w-100 mt-10 my-btn" @click="next">Redeem Reward</v-btn>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  mounted(){
    liff.init({
      liffId: '2000874237-bkE4ZdVn'
    }).then(() => {
      if(liff.isLoggedIn()){
        liff.getProfile().then(profile => {
          this.$store.dispatch('setLine', profile);
          this.$axios.get(`https://doonungonline-gm-default-rtdb.firebaseio.com/members/${this.$store.getters.getLine.userId}/profile.json`).then((res) => {            
            if(res.data != null){
              this.$store.dispatch('setUser', res.data);
            }
          });
          this.$axios.get(`https://doonungonline-gm-default-rtdb.firebaseio.com/rewards/${this.$store.getters.getLine.userId}.json`).then((res) => {            
            if(res.data != null){
              this.stamps = res.data
            }
          });
        })
      }else{
        liff.login();
      }
    })
  },
  computed: {
    getLine(){
      return this.$store.getters.getLine;
    },
    getUser(){
      return this.$store.getters.getUser;
    },
    isDone(){
      let isDone = true;
      this.stamps.forEach(ele => {
        if(ele.value === false){
          isDone = false;
          return isDone;
        }
      })
      return isDone;
    }
  },
  methods: {
    scan(){
      liff.scanCode().then(result => {
        this.stamps = this.stamps.map((obj) => {
          if(obj.name == result.value){
            obj.value = true;
          }
          return obj;
        })
        this.$axios.patch(`https://doonungonline-gm-default-rtdb.firebaseio.com/rewards/${this.$store.getters.getLine.userId}.json`, {...this.stamps}).then((res) => {            

        }).catch(e => alert(e))
      }).catch(e => alert(e))
    },
    next(){
      this.$router.push('reward/done');
    }
  },
  data(){
    return {
      stamps: [
        {
          name: 'stamp1',
          value: false
        },
        {
          name: 'stamp2',
          value: false
        },
        {
          name: 'stamp3',
          value: false
        },
        {
          name: 'stamp4',
          value: false
        },
        {
          name: 'stamp5',
          value: false
        },
        {
          name: 'stamp6',
          value: false
        },
        {
          name: 'stamp7',
          value: false
        },
        {
          name: 'stamp8',
          value: false
        }     
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  .name{
    margin-left: 20px;
    font-size: 20px;
  }
  .v-card__text{
    padding: 10px 15px;
  }
  .stamp-zone{
    background: #BDBDBD;
    padding: 25px 25px 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
  .stamp{
    flex-basis: 25%;
  }
  .circle{
    background: #FFF;
    border-radius: 50%;
    border: 2px #ff168a solid;
    height: 55px;
    width: 55px;    
    justify-content: center;
    display: inline-flex;
    margin-bottom: 25px;    
    .v-icon{
      display: none;
    }
    &.active{
      background: #ff168a;
      span{
        display: none;
      }
      .v-icon{
        display: flex;
        color: #FFF;
      }
    }
    &.end{
      background: #ff168a;
      span{
        font-size: 16px;        
        color: #FFF;
      }
    }
    span{
      align-self: center;
      font-size: 20px;
      color: #ff168a;
      font-weight: bold;
    }
  }
  .scan{
    svg{
      margin-right: 5px;
    }
  }
</style>
