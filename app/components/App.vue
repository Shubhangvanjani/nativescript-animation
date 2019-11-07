<template>
    <Page>
        <ActionBar>
            <GridLayout width="100%" columns="*, *, *">
                <Label class="fa" :text="'fa-bars' | fonticon" ref="menuBar" bageValue=4  @tap="barClick" col="0"/>
                <!-- <Label class="title" text="Welcome to NativeScript-Vue!"  col="1"/> -->
                <!-- <BadgeButton text="Button" badgeValue="1" badgeOriginX="450" /> -->
                <Label class="fa" :text="'fa-bell' | fonticon" ref="notificationBell"  @tap="notificationTap" horizontalAlignment=center  col="2"/>
                <Label class="fa" :text="'fa-power-off' | fonticon"  @tap="$refs.drawer.nativeView.showDrawer()" horizontalAlignment=right style="margin-right:50px;" col="2"/>
            </GridLayout>
        </ActionBar>

        <RadSideDrawer ref="drawer">
            <StackLayout ~drawerContent backgroundColor="#ffffff">
                <Label class="drawer-header" text="Drawer"/>

                <Label class="drawer-item" text="Item 1"/>
                <Label class="drawer-item" text="Item 2"/>
                <Label class="drawer-item" text="Item 3"/>
            </StackLayout>

            <GridLayout ~mainContent columns="*" rows="*">
                <!-- <Label class="message" :text="msg" col="0" row="0"/> -->
                <WebView src="https://auth.flowzcluster.tk/auth/salesforce" />
            </GridLayout>
        </RadSideDrawer>
    </Page>
</template>

<script >
  export default {
    data() {
      return {
        msg: 'Hello World!'
      }
    },
    methods: {
        notificationTap(){
            console.log("Called")
            // this.$refs.notificationBell.nativeView
            // .animate({
            //     rotate: 45,
            //     duration: 1000
            // }).then(() => {
                
            // })
            var animation1 = this.$refs.notificationBell.nativeView.createAnimation({ rotate: 45, duration: 500 })
            var animation2 = this.$refs.notificationBell.nativeView.createAnimation({ rotate: -45, duration: 500 })
            var animation3 = this.$refs.notificationBell.nativeView.createAnimation({ rotate: 0})
            animation1.play()
                .then(function () { return animation2.play(); })
                .then(function () { return animation1.play(); })
                .then(function () { return animation2.play(); })
                .then(function () { return animation1.play(); })
                .then(function () { return animation2.play(); })
                .then(function () {
                console.log("Animation finished");
                return animation3.play();
            })
        },
        barClick(){
            let animation1 = this.$refs.menuBar.nativeView.createAnimation({ opacity:0.5, duration: 200 })
            let animation2 = this.$refs.menuBar.nativeView.createAnimation({ opacity:1, duration: 500 })
            animation1.play().then(() => {
               return animation2.play() 
            })
            this.$refs.drawer.nativeView.showDrawer()
        }
    },
    mounted(){
        // this.$refs.notificationBell.nativeView
        // .animate({
        //      opacity: 0,
        //     duration: 3000
        // })
        var animation1 = this.$refs.notificationBell.nativeView.createAnimation({ rotate: 45, duration: 500 })
            var animation2 = this.$refs.notificationBell.nativeView.createAnimation({ rotate: -45, duration: 500 })
            var animation3 = this.$refs.notificationBell.nativeView.createAnimation({ rotate: 0})
            animation1.play()
                .then(function () { return animation2.play(); })
                .then(function () { return animation1.play(); })
                .then(function () { return animation2.play(); })
                .then(function () { return animation1.play(); })
                .then(function () { return animation2.play(); })
                .then(function () {
                console.log("Animation finished");
                return animation3.play();
            })
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }   
    .fa{
        font-size: 20px;    
    }

    .title {
        text-align: left;
        padding-left: 16;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }

    .drawer-header {
        padding: 50 16 16 16;
        margin-bottom: 16;
        background-color: #53ba82;
        color: #ffffff;
        font-size: 24;
    }

    .drawer-item {
        padding: 8 16;
        color: #333333;
        font-size: 16;
    }
</style>
