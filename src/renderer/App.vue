<template>
    <div id='app'>
        <router-view></router-view>
    </div>
</template>

<script type="text/ecmascript-6">
    export default {
        name: 'vocabook',
        watch: {
            '$store.state.config.theme' (value) {
                document.body.className = value
            }
        },
        mounted () {
            document.body.className = this.$store.state.config.theme
            this.$electron.ipcRenderer.on('message', (event, arg) => {
                console.log(`%c ${arg}`, 'font-size:13px;color:red;')
            })
        }
    }
</script>

<style lang="scss">
    /* global css */
    @import '../../node_modules/font-awesome/css/font-awesome.css';
    @import '../../node_modules/normalize.css/normalize.css';
    @import './styles/theme.css';
    @import './styles/animates.css';

    html, body, #app {
        height: 100%;
    }

    /* app-related css have 'app-' prefix */
    .app-drag {
        -webkit-app-region: drag;
        user-select: none;
        cursor: default;
    }

    .app-non-drag {
        -webkit-app-region: no-drag;
    }

    /* common css */

    .non-select {
        user-select: none;
    }

    ::-webkit-scrollbar{
        width: 0;
        height: 0;
    }

    .txt-ellipsis {
        display: block;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .hand {
        cursor: pointer;
    }

    .full-height {
        height: 100%;
    }

    .full-width {
        width: 100%;
    }

    .padding5 {
        padding: 5px;
    }

    .clearfix {
        &:after {
            display: block;
            clear: both;
            content: "";
        }
    }
    .flex {
        display: flex;
    }

    .heart {
        color: var(--major)
    }
</style>
