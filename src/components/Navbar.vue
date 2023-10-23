<template>
    <nav>
        <ul class="content">
            <li class="logo">
                <a href="">
                    <img src="https://store.akamai.steamstatic.com/public/shared/images/header/logo_steam.svg?t=962016"
                        width="176" height="44">
                </a>
            </li>

            <li class="selects" v-for="(item, index) in menuItems" :key="index" @mouseleave="hideDropDown"
                @mouseover="showDropDown(item.name, index)">
                <a :href="item.link" :class="{ active: isActive(item.link) }">{{ item.name }}</a>
                <transition name="fade">
                    <ul @mouseleave="hideDropDown" v-if="activeMenu === index" class="dropdown">
                        <li v-for="(dropItem, dropIndex) in shopDropDown" :key="'drop' + dropIndex">
                            <a href="#">{{ dropItem }}</a>
                        </li>
                    </ul>
                </transition>
                <transition name="fade">
                    <ul @mouseleave="hideCommunityDropDown" v-if="CommunityDropDown === index" class="dropdown">
                        <li v-for="(dropItem, dropIndex) in community" :key="'drop' + dropIndex">
                            <a href="#">{{ dropItem }}</a>
                        </li>
                    </ul>
                </transition>
            </li>

            <li class="others">
                <ul>
                    <li><button>安装 Steam</button></li>
                    <li><a href="" style="padding-right: 13px; border-right: 2px solid rgb(98, 98, 98);">登录</a></li>
                    <li @click="toggleMenu">语言<svg t="1697951686857" style="position: relative; top: 4px; left: 3px;"
                            class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
                            p-id="7326" width="10" height="10">
                            <path d="M156.692-0.653l355.308 388.447 355.355-388.447z" fill="#CCCCCC" p-id="7327"></path>
                        </svg>
                        <transition name="fade">
                            <ul v-if="showLanguageMenu" class="dropdown" style="position: absolute;
    top: 35px;">
                                <li v-for="language in languages" :key="language"><a style="padding: 10px 45px;" href="">{{
                                    language }}</a></li>
                            </ul>
                        </transition>
                    </li>
                </ul>
            </li>
        </ul>
    </nav>
</template>
<script>
export default {
    name: "Navbar",
    methods: {
        isActive(link) {
            return window.location.href.endsWith(link);
        },
        toggleMenu() {
            this.showLanguageMenu = !this.showLanguageMenu;
        },
        showDropDown(name, index) {
            if (name === '商店') {
                this.activeMenu = index;
            } else if (name === '社区') {
                this.CommunityDropDown = index;
            }
        },
        hideDropDown() {
            this.activeMenu = null;
            this.CommunityDropDown = null;
        },
        hideCommunityDropDown() {
            this.CommunityDropDown = null;
            this.activeMenu = null;
        }
    },
    data() {
        return {
            showLanguageMenu: false,
            shopDropDown: ['主页', '探索队列', '愿望队列', '愿望单', '点数商店', '新闻', '统计数据'],
            community: ['主页', '讨论', '创意工坊', '市场', '实况直播'],
            languages: ['繁體中文(繁體中文)', '日本語(日语)', '한국어(韩语)', 'English(英语)', 'แบบไทย(泰语)', 'български(保加利亚语)', 'čeština(捷克语)', 'Dansk(丹麦语)', 'Deutsch(德语)', 'español(西班牙语)', 'Ελληνικά(希腊语)', 'Français(法语)', 'Italiano(意大利语)', 'Magyar(匈牙语)', 'Nederlands(荷兰语)', 'norsk(挪威语)', 'svenska(瑞典语)', 'русский язык(俄语)', 'Română(罗马西亚语)', 'suomi(芬兰语)', 'svenska(svenska)', 'Türkçe(土耳其语)', 'Tiếng Việt(越南语)', 'Українська(乌克兰语)'],
            menuItems: [
                { name: '商店', link: '/' },
                { name: '社区', link: '/community' },
                { name: '关于', link: '/about' },
                { name: '客服', link: '/server' },
            ],
            activeMenu: null,
            CommunityDropDown: null
        }
    }
}
</script>
  
<style lang="css">


.active {
    color: rgb(26,159,255);
    text-decoration: none;
    border-bottom: 3px solid rgb(26,159,255);
    padding-bottom: 2px;
}

.others {
    margin-top: 6px;
    margin-left: 327px;
}


.others li,
button {
    color: #cfcfcf;
    font-size: 11px;
    font-family: "Motiva Sans", Sans-serif;
}

.others button {
    background-color: #5C7E10;
    width: 101.48px;
    height: 27px;
    color: #e5e4dc;
    font-weight: normal;
    display: inline-block;
    background-position: 12px 7px;
    background-image: url(https://store.akamai.steamstatic.com/public/shared/images/header/btn_header_installsteam_download.png?v=1);
    background-repeat: no-repeat;
    padding-left: 26px;
    border: none;
    text-align: center;
}

nav {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 104px;
}

nav ul {
    list-style-type: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin-right: 13px;
}

nav ul li a {
    text-decoration: none;
    color: rgb(217, 217, 217);
    font-weight: inherit;
}

nav ul li a:hover {
    color: #ffffff;
}

.content {
    color: #C6D4DF;
    font-family: 14px "Motiva Sans", sans-serif;
    background: #171D25;
    width: 940px;
    height: 104px;
    display: flex;
    justify-content: flex-start;
}

.logo {
    font-family: 14px "Motiva Sans", sans-serif;
    margin: 0px 40px 0px 0px;
    padding: 30px 0px 0px;
    color: #C6D4DF;
    width: 170px;
    height: 74px;
}

.selects {
    margin-top: 43px;
}

.dropdown {
    display: flex;
    flex-direction: column;
    background-color: rgb(61, 68, 80);
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    z-index: 1;
    position: absolute;
    top: 69px;
}

.dropdown li {
    background-color: rgb(61, 68, 80);
    width: 100%;
}

.dropdown a {
    color: rgb(234, 234, 234);
    padding: 6px 8px;
    text-decoration: none;
    display: block;
    font-size: 12px;
}

.dropdown li:hover {
    background-color: #f1f1f1;
}

.dropdown a:hover {
    color: #171D25;
}

.fade-enter-active {
    transition: opacity 0.23s;

}

.fade-leave-active {
    transition: opacity 0.33s;
}

.fade-enter-active,
.fade-leave-to {
    opacity: 0;
}</style>
