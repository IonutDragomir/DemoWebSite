<template>
    <div class="main-container">
        <div class="logo-container">
            <img src="../assets/logo.svg" alt="logo">
        </div>
        <div class="menu-container">
            <div>
                <p>About Us</p>
                <img src="../assets/arrow-right.svg" alt="arrow-right">
            </div>
            <div>
                <p class="current">Gallery</p>
            </div>
            <div>
                <p>Crew</p>
                <img src="../assets/arrow-right.svg" alt="arrow-right">
            </div>
            <div>
                <p>Contact</p>
                <img src="../assets/arrow-right.svg" alt="arrow-right">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HeaderComp'
}
</script>
<style lang="scss">
.main-container {
    display: flex;
    flex-direction: row;
    width: 100%;
    margin-bottom: -4vw;
    z-index: 100;
    position: sticky;
    border-bottom: 1.5px solid rgb(189, 189, 189);

    .logo-container {
        height: 7vh;
        width: 50%;
        display: flex;
        align-content: center;
        align-items: center;
        justify-content: center;
        width: 25%;
    }

    .menu-container {
        height: 7vh;
        width: 50%;
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        align-items: center;
        color: #fff;
        margin-left: 20vw;

        div {
            display: flex;
            flex-direction: row;
            height: 100%;
            align-items: center;
            justify-content: center;

            img {
                margin-left: 16px;
                width: 24px;
                opacity: 0;
            }
        }

        div:hover img,
        div:hover p {
            opacity: 1;
        }

        div:hover {
            animation: fadeIn 0.5s forwards;
            cursor: pointer;
        }

        div:not(:hover) {
            animation: fadeOut 0.5s forwards;
        }

        p {
            font-size: 22px;
            font-weight: 700;
            opacity: 0.5;
            text-transform: uppercase;
        }

        .current {
            opacity: 1;
        }
    }
}

@keyframes fadeIn {
    0% {
        background: none;
        width: 16%;
    }

    100% {
        background: #C4132F;
        width: 20%;
    }
}

@keyframes fadeOut {
    0% {
        background: #C4132F;
        width: 20%;
    }

    100% {
        background: none;
        width: 16%;
    }
}

@media screen and (max-width: 431px) {
    .main-container {

        .logo-container {
            img {
                height: 4vw;
            }
        }

        .menu-container {
            margin-left: 5vw;
            width: 74%;

            p {
                font-size: 1.5vw;
                text-align: center;
            }

            div {
                margin-right: -15.6vw;

                img {
                    margin-left: 1vw;
                    width: 2.5vw;
                }
            }



            div {
                height: 11.5vw;
            }

        }

        .menu-container:last-child {
            margin-right: 0vw;
        }
    }
}
</style>
