<template>
    <div class="text-container">
        <section>
            <h2>This is headline</h2>
            <p>Subtitle goes here</p>
        </section>
        <article>
            <p>Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam
                rem
                aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt
                explicabo.
                Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni
                dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia
                dolor
                sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et
                dolore
                magnam aliquam quaerat voluptatem.</p>

        </article>
        <article class="second">
            <p>
                Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et
                dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip
                ex
                ea commodo consequat.

                Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est
                laborum.
            </p>

        </article>
    </div>
    <div class="black-section">
        <img src="../assets/visual.jpg" alt="boat">
    </div>
</template>

<script>

export default {
    name: 'TextSection'
}
</script>
<style lang="scss">
.text-container {
    background-color: #fff;
    height: 80vh;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;

    section {
        width: 20%;
        margin-bottom: 14vw;

        h2 {
            font-weight: 800;
            font-size: 60px;
            line-height: 72px;
            text-transform: uppercase;
        }

        p {
            font-size: 24px;
            font-weight: 700;
            line-height: 29px;
            text-transform: uppercase;
        }

    }

    article {
        width: 20%;
        margin-bottom: 14vw;

        p {
            font-size: 16px;
            font-weight: 700;
            line-height: 28.8px;
            height: 20vh;
        }
    }

    .second {
        margin-right: 3vw;
    }

}


.black-section {
    height: 21vh;
    width: 100%;
    background: #181818;
    position: relative;

    img {
        position: absolute;
        top: -16vh;
        right: 0vw;
    }
}

@media screen and (max-width: 431px) {
    .text-container {

        section {
            margin-bottom: 62vw;

            h2 {
                font-size: 4vw;
                line-height: 4vw;
            }

            p {
                font-size: 3vw;
                line-height: 3vw;
            }

        }

        article {

            p {
                font-size: 2vw;
                line-height: 2vw;
                height: 40vh;
            }
        }

    }

    .black-section {

        img {
            top: -8vh;
            height: 30vw;
        }
    }
}
</style>