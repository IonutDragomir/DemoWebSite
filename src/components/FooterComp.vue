<template>
    <div class="footer-container">
        <div class="logo">
            <img src="../assets/logo.svg" alt="logo">
            <p>© 2021. Segel-Team. Alle Rechte vorbehalten</p>
        </div>
        <div class="menu-container">
            <div class="menu">
                <div class="left-row">
                    <p>About Us</p>
                    <p>Gallery</p>
                    <p>Crew</p>
                    <p>Contact</p>
                </div>
                <div class="right-row">
                    <p>Impressum</p>
                    <p>Datenschutz</p>
                    <p>Rechtliches</p>
                    <p>Copyright</p>
                </div>
            </div>
            <div class="icons">
                <span>
                    <img src="../assets/facebook.svg" alt="facebook-icon">
                </span>
                <span>
                    <img src="../assets/twitter.svg" alt="twitter-icon">
                </span>
                <span>
                    <img src="../assets/instagram.svg" alt="instagram-icon">
                </span>
                <span>
                    <img src="../assets/youtube.svg" alt="youtube-icon">
                </span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'FooterComp'
};
</script>
<style lang="scss">
.footer-container {
    // height: 25vw;
    width: 100%;
    display: flex;
    flex-direction: row;


    .logo,
    .menu {
        display: flex;
        flex-direction: column;
    }

    .logo {
        background-color: #181818;
        height: 100%;
        width: 55%;
        color: #fff;
        padding: 5vw;
        box-sizing: border-box;

        img {
            width: 55%;
        }

        p {
            margin-top: 12vw;
        }
    }

    .menu-container {
        background-color: #C4132F;
        height: 100%;
        width: 50%;
        padding: 5vw;
        box-sizing: border-box;

        .menu {
            display: flex;
            flex-direction: row;
            justify-content: space-around;
            color: #fff;
            margin-left: -5vw;

            p {
                font-size: 20px;
                margin: 30px;
                cursor: pointer;
            }

            .right-row {
                margin-left: -12vw;
            }
        }

        .icons {
            display: flex;
            flex-direction: row;
            justify-content: space-around;
            width: 63%;
            margin-top: 4.47vw;
            margin-left: 4vw;

            span {
                margin-right: 1vw;
            }
        }
    }

    @media screen and (max-width: 431px) {
        .footer-container {
            height: auto;
        }

        .logo p {
            font-size: 1vw;
            margin-top: 21.7vw;
        }

        .menu-container {
            .menu p {
                font-size: 2vw;
                margin: 2vw;
            }

            .icons span img {
                height: 3vw;
            }
        }

    }
}
</style>