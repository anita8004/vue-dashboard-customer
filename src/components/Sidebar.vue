<template>
  <nav class="col-md-2 d-none d-md-block bg-dark sidebar">
    <div class="sidebar-sticky">
      <ul class="nav flex-column">
        <li class="nav-item">
          <router-link to="/admin/applist" class="nav-link active" v-if="userCanRead.applist" role="applist">
            <span class="icon-th-thumb"></span>
            APP 平台
          </router-link>
        </li>
        <li class="nav-item" v-if="userCanRead.member" role="member">
          <router-link to="/admin/members" class="nav-link">
            <span class="icon-user"></span>
            使用者管理
          </router-link>
        </li>
        <li class="nav-item" v-if="userCanRead.competence" role="competence">
          <router-link to="/admin/competence" class="nav-link">
            <span class="icon-cog"></span>
            權限管理
          </router-link>
        </li>
        <li class="nav-item" v-if="userCanRead.records" role="records">
          <router-link to="/admin/records" class="nav-link">
            <span class="icon-record"></span>
            操作紀錄
          </router-link>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
import firebase from 'firebase'
import $ from 'jquery'
export default {
  name: 'Sidebar',
  data () {
    return {
      userCanRead: {
        applist: true,
        member: false,
        competence: false,
        records: false
      },
      thisPageName: ''
    }
  },
  methods: {
    decideUserCanRead (num) {
      switch (num) {
        case 0:
          return true
        default:
          return false
      }
    },
    getPageName (path) {
      var index = path.lastIndexOf('/') +1
      return path.slice(index)
    }
  },
  mounted () {
    const vm = this
    firebase.auth().onAuthStateChanged(function (user) {
      if (user) {
        vm.$db.ref('member/currentUser').orderByChild('uid').equalTo(user.uid).on('value', snapshot => {
          let data = snapshot.val()
          for (let key in data) {
            let value = data[key]
            vm.userCanRead = value.readPage
          }
        })
      } else {
        // No user is signed in.
      }
    })
  }
}
</script>
