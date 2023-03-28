<template>
    <div class="btn-group" v-on-clickaway="close"  v-bind:class="{focus: showMenu }">
        <li v-if="selected!==''" @click="toggleMenu()" v-on:click="clicktimot()" class="dropdown-toggle" v-bind:class="{ open: showTimeOut, focus: showMenu }"  >
            {{ mapState!==null?mapState[selectedOption]:selectedOption}}
            <svg  width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M1.53246 0.2661L5.00466 3.80169L8.47687 0.2661C8.55972 0.181736 8.65808 0.114815 8.76633 0.0691577C8.87458 0.0235002 8.9906 8.88921e-10 9.10777 0C9.22494 -8.88916e-10 9.34096 0.0235002 9.44921 0.0691577C9.55746 0.114815 9.65582 0.181736 9.73867 0.2661C9.82152 0.350464 9.88724 0.450618 9.93208 0.560845C9.97692 0.671072 10 0.789212 10 0.908521C10 1.02783 9.97692 1.14597 9.93208 1.2562C9.88724 1.36642 9.82152 1.46658 9.73867 1.55094L5.63109 5.73351C5.5483 5.81799 5.44996 5.88501 5.3417 5.93074C5.23345 5.97646 5.11739 6 5.00019 6C4.88299 6 4.76693 5.97646 4.65868 5.93074C4.55042 5.88501 4.45208 5.81799 4.36929 5.73351L0.261707 1.55094C0.178747 1.46664 0.112929 1.36651 0.0680222 1.25627C0.023115 1.14604 0 1.02786 0 0.908521C0 0.789178 0.023115 0.671007 0.0680222 0.560771C0.112929 0.450536 0.178747 0.350402 0.261707 0.2661C0.610717 -0.0801698 1.18345 -0.0892821 1.53246 0.2661Z" fill="#AFAFAF"/>
            </svg>

        </li>
        <li v-else @click="toggleMenu()" v-on:click="clicktimot()" v-bind:class="{ open: showTimeOut, focus: showMenu , warning: warning}" class="dropdown-toggle placeholder" >
            {{ mapState!==null?mapState[placeholderText]:placeholderText}}
            <svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M1.53246 0.2661L5.00466 3.80169L8.47687 0.2661C8.55972 0.181736 8.65808 0.114815 8.76633 0.0691577C8.87458 0.0235002 8.9906 8.88921e-10 9.10777 0C9.22494 -8.88916e-10 9.34096 0.0235002 9.44921 0.0691577C9.55746 0.114815 9.65582 0.181736 9.73867 0.2661C9.82152 0.350464 9.88724 0.450618 9.93208 0.560845C9.97692 0.671072 10 0.789212 10 0.908521C10 1.02783 9.97692 1.14597 9.93208 1.2562C9.88724 1.36642 9.82152 1.46658 9.73867 1.55094L5.63109 5.73351C5.5483 5.81799 5.44996 5.88501 5.3417 5.93074C5.23345 5.97646 5.11739 6 5.00019 6C4.88299 6 4.76693 5.97646 4.65868 5.93074C4.55042 5.88501 4.45208 5.81799 4.36929 5.73351L0.261707 1.55094C0.178747 1.46664 0.112929 1.36651 0.0680222 1.25627C0.023115 1.14604 0 1.02786 0 0.908521C0 0.789178 0.023115 0.671007 0.0680222 0.560771C0.112929 0.450536 0.178747 0.350402 0.261707 0.2661C0.610717 -0.0801698 1.18345 -0.0892821 1.53246 0.2661Z" fill="#AFAFAF"/>
            </svg>

        </li>
        <TransitionExpand>
            <ul class="dropdown-menu-render" v-show="showMenu"  v-bind:class="{ open: showMenu }">
                <li v-for="(option, idx) in options" :key="idx">
                    <a href="javascript:void(0)" @click="updateOption(option)">
                        {{ mapState!==null?mapState[option]:option}}
                    </a>
                </li>

            </ul>
        </TransitionExpand>
    </div>
</template>

<script>
    import TransitionExpand from '@/components/TransitionExpand.vue';
    import {mixin as clickaway} from 'vue-clickaway';
    export default {
        components:{TransitionExpand},
        mixins: [ clickaway ],
        data() {
            return {
                selectedOption: '',
                showMenu: false,
                showTimeOut: false,
                placeholderText: '',
            }
        },
        watch: {
            'options': function () {
                if(this.firstItem ){
                    this.selectedOption = this.options[0];
                    this.$emit('updateOption', this.selectedOption);
                    this.$emit('update:selected', this.options[0].value);
                }
            },'selected': function (now) {
                if(now!=='') {
                    this.selectedOption =now
                }
            }
        },
        props: {
            type:{default:''},
            options: {},
            warning:{default:''},
            selected: {default:''},
            mapState:{default: null},
            firstItem: {
                type: [Boolean],
                default: false,
            },
            placeholder: [String],
            closeOnOutsideClick: {
                type: [Boolean],
                default: true,
            },
        },
        mounted() {
            this.selectedOption = this.selected;
            if (this.placeholder)
            {
                this.placeholderText = this.placeholder;
            }

        },
        beforeDestroy() {
            document.removeEventListener('click', this.clickHandler);
        },
        methods: {
            close(){
                this.showMenu=false;
            },
            updateOption(option) {
                    this.selectedOption = option;
                    this.showMenu = false;
                    this.$emit('update:selected', option);
                    this.clicktimot();

            },
            toggleMenu() {
                this.showMenu = !this.showMenu;
            },
            clickHandler(event) {
                const { target } = event;
                const { $el } = this;
                if (!$el.contains(target)) {
                    this.showMenu = false;
                    this.clicktimot();
                }
            },
            clicktimot(){
                //this.showTimeOut =!this.showMenu;
                if(this.showTimeOut === false){
                    //this.showTimeOut=true;
                }else{

                    setTimeout(()=>{
                        this.showTimeOut=false
                    },500);
                }
            }
        }
    }
</script>

<style lang="scss">
    .btn-group {
        width: 100%;
        position: relative;
        display: inline-block;
        vertical-align: middle;
    }
    .btn-group a:hover {
        text-decoration: none;
    }
    .dropdown-toggle {
        text-align: center;
        position: relative;
        padding: 7px 19px;
        text-transform: none;
        margin-bottom: 7px;
        background: #FFFFFF;
        box-sizing: border-box;
        border-radius: 7px;
        transition: background 0s ease-out;
        float: none;
        display: flex;
        justify-content: center;
        align-items: center;
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow: hidden;
        font-weight: 500;
        font-size: 14px;
        line-height: 20px;
        svg{
            margin-left: 5px;
            transition: all .3s;
            transform: rotate(0deg);
        }
        &.warning{
            &.focus{
                border: 2px solid #DFE0E1;
            }
            border: 2px solid #FF4B58;
        }
        &.focus{
            svg{
                transform: rotate(180deg);
            }
        }
        &.open{

            border-radius: 7px 7px 0 0;
            border: 2px solid #DFE0E1;
        }
        &.placeholder{

            font-weight: 500;
            font-size: 14px;
            line-height: 20px;
            letter-spacing: 0.02em;
            color: #D1D1D1;
        }
        .icon-time{
            position: absolute;
            right: 13px;
            top: 14px;
            width: 22px;
            height: 22px;
            z-index: 11;
        }
        .icon-finmoll-arrow-right{
            float: right;
            transform: rotate(90deg);
            transition: transform .1s;
            fill: #1C1C1C;
            width: 18px;
            height: 18px;

            &.open{

                transform: rotate(-90deg);
                transition: transform .1s;
            }
        }
    }
    .dropdown-menu-render {
        position: absolute;
        top: 100%;
        width: 100%;
        right: 0;
        z-index: 12;
        float: left;
        padding: 5px 0;
        list-style: none;
        font-size: 12px;
        line-height: 20px;
        letter-spacing: 0.02em;
        text-align: left;
        background-color: #EBEBEB;
        background-clip: padding-box;
        border-top: none;
        max-height: 190px;
        overflow: auto;
        text-align: center;
        &.open{
            max-height: 190px;
            overflow: auto;
        }

    }
    .dropdown-menu-render > li > a {
        padding: 11px 17px;
        display: block;
        clear: both;
        font-weight: normal;
        white-space: normal;
        text-decoration: none;
        font-size: 12px;
        line-height: 20px;
        letter-spacing: 0.02em;
        color: #1C1C1C;

        @media(min-width: 768px) {
            white-space: nowrap;
            font-size: 12px;
            line-height: 20px;
            letter-spacing: 0.02em;
        }
    }
    .dropdown-menu-render > li > a:hover {
        background: #D9D9D9;
    }
    .dropdown-menu-render > li {
        overflow: hidden;
        width: 100%;
        position: relative;
        margin: 0;
        &.archive{
            a {
                color: #bdbdbd;
            }
        }
    }
    .caret {
        width: 0;
        position: absolute;
        top: 19px;
        height: 0;
        margin-left: -24px;
        vertical-align: middle;
        border-top: 4px dashed;
        border-top: 4px solid \9;
        border-right: 4px solid transparent;
        border-left: 4px solid transparent;
        right: 10px;
    }
    li {
        list-style: none;
    }

</style>
