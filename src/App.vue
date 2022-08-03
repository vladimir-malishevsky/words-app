<template>
  <div class="wrapper">
    <div class="sidebar">
        <router-link class="sidebar__nav-element" to="/">
          <i class="fas fa-home-alt"></i>
        </router-link>
    </div>
    <div class="content"><router-view/></div>
  </div>
</template>

<style lang="scss">
@import "assets/scss/Mixins/BreakpointsMixin";

*, *:before, *:after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.wrapper {
  width: 100%;
  height: auto;
  display: flex;
  @include sm {
    flex-direction: column;
  }

  .sidebar {
    width: 50px;
    height: 100vh;
    padding-top: 10px;
    background: #FDFDFD;
    display: flex;
    flex-direction: column;
    align-items: center;
    @include sm {
      padding: 0;
      width: 100%;
      height: 50px;
      flex-direction: row;
      justify-content: center;
    }

    .sidebar__nav-element {
      width: 50px;
      height: 40px;
      line-height: 40px;
      text-decoration: none;
      text-align: center;
      transition: font-size 0.2s;
      @include sm {
        height: 50px;
        line-height: 50px;
      }
      &:hover {
        font-size: 18px;
      }
    }
  }

  .content {
    flex: 1 0;
    //min-height: 100vh;
  }
}


</style>
