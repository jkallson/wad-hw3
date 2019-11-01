<template>
    <main id="app">
        <Header></Header>
        <section id="container">
            <section id="main">
                <div class="content">
                    <Profile :class="{active: activeTabName === 'Profile'}" :profile="profile"></Profile>
                    <Courses :class="{active: activeTabName === 'Courses'}"></Courses>
                </div>

                <div class="controls">
                    <button @click="setActiveTabName('Profile')" id="profile-button" class="pill" :class="{active: activeTabName === 'Profile'}">Profile</button>
                    <button @click="setActiveTabName('Courses')" id="courses-button" class="pill" :class="{active: activeTabName === 'Courses'}">Courses</button>
                </div>
            </section>
        </section>
        <Footer></Footer>
    </main>
</template>

<script>
    import Header from "./components/Header";
    import Footer from "./components/Footer";
    import Profile from "./components/Profile";
    import User from "./models/User";
    import Courses from "./components/Courses";
    export default {
        name: 'app',
        components: {
            Courses,
            Profile,
            Header,
            Footer
        },
        data: () => {
            return{
                activeTabName: "Profile",
                profile: new User("Ahto","Leemet","17/06/1996","Software Engineering")
            }
        },
        methods: {
            setActiveTabName(name) {
                this.activeTabName = name;
            }
        },

    }
</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Livvic', sans-serif;
    }

    html, body {
        padding: 0;
        margin: 0;
        width: 100%;
        height: 100%;
        background-color: #eaeaea;
    }

    main {
        position: relative;
        min-height: 100%;
        padding-bottom: 110px;
    }
    #container {
        width: 80%;
        max-width: 900px;
        min-width: 320px;
        padding: 15px;
        background-color: #ffffff;
        margin: 0 auto;
    }

    .content {
        padding: 10px;
        border: 1px solid #cbcbcb;
    }

    table {
        width: 100%;
        border-collapse: collapse;

    }

    table th {
        padding: 8px 12px;
        text-align: left;
        border: 1px solid #cbcbcb;
        background-color: #03A9F4;
        color: #ffffff;
    }

    table td {
        padding: 8px 12px;
        border: 1px solid #cbcbcb;
    }

    .content .tab {
        display: none;
    }

    .content .tab.active {
        display: block;
    }

    .controls .pill {
        border: 1px solid #cbcbcb;
        background-color: #eaeaea;
        padding: 10px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: none;
        margin-top: -1px;
        outline: none !important;
    }

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .controls .pill:hover {
        cursor: pointer;
    }

    .blue-button {
        background-color: #2196F3;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .green-button {
        background-color: #69f378;
        color: #ffffff;
        border: none;
        padding: 10px 10px;
    }

    .grey-button {
        background-color: #e1e8e6;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .input {
        border: 1px solid #cccccc;
        padding: 10px 20px;
        min-width: 135px;
    }

    #add-course {
        display: none;
    }
</style>
