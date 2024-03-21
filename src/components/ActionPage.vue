<template>
    <div class="action-container">
        <div class="title-container">
            <div class="title">
                <h2>unser team</h2>
                <p>Subtitle goes here</p>
            </div>
            <div class="filters">
                <p @click="filterValue = 'all'">Show All</p>
                <p @click="filterValue = 'trim'">Trim</p>
                <p @click="filterValue = 'tactic'">Tactic</p>
                <p @click="filterValue = 'helmsman'">HELMSMANN</p>
            </div>
        </div>

        <div class="pictures">
            <div class="crew-member"
                :class="{ 'four-pictures': pictureNumber === 4, 'five-pictures': pictureNumber === 5, 'six-pictures': pictureNumber === 6 }"
                v-for="(member, index) in filterPhotoRow(filterValue)" :key="member.id">
                <div class="facts"
                    :class="{ 'four-pictures': pictureNumber === 4, 'five-pictures': pictureNumber === 5, 'six-pictures': pictureNumber === 6, 'last-photo': (index + 1) % pictureNumber === 0 }">
                    <div></div>
                    <div>
                        <p class="name">{{ member.name }}</p>
                        <p class="quote">A smooth sea never made a skilled sailor</p>
                        <p class="duties">{{ member.duties }}</p>
                    </div>
                </div>
                <img :class="{ 'four-pictures': pictureNumber === 4, 'five-pictures': pictureNumber === 5, 'six-pictures': pictureNumber === 6 }"
                    :src="member.image" :alt="member.name">
            </div>
        </div>

        <div class="buttons">
            <div class="columns">
                <span @click="pictureNumber = 4" :class="{ 'selected': pictureNumber === 4 }">4</span>
                <span @click="pictureNumber = 5" :class="{ 'selected': pictureNumber === 5 }">5</span>
                <span @click="pictureNumber = 6" :class="{ 'selected': pictureNumber === 6 }">6</span>
            </div>
            <div class="load">
                <button @click="++rowNumber, loadMore()">
                    Load More
                </button>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'ActionPage',
    data() {
        return {
            storedData: '', // Store the fetched crew members data
            pictureNumber: 5, // Number of crew members per row
            rowNumber: 1, // Number of rows
            storeData: [], // Temporary storage for fetched data
            filterValue: "all" // Default filter value
        }
    },
    methods: {
        // Fetch crew members data asynchronously
        async getData() {
            try {
                let url = 'https://challenge-api.view.agentur-loop.com/api/?page=' + this.rowNumber + '&limit=6';
                let response = await axios.get(url, {
                    headers: {
                        Authorization: 'Bearer 0123456789'
                    }
                });
                // Push the fetched data into the temporary storage
                this.storeData.push(response.data.data.data);
                // Flatten the nested arrays and store them
                this.storedData = this.storeData.flat();
            } catch (error) {
                throw new Error('Error fetching crew members:', error);
            }
        },
        // Filter crew members based on the selected duty value
        filterPhotoRow(filterValue) {
            if (filterValue === 'all') {
                // If "show all" is selected, return the original data
                return this.storedData.slice(0, this.rowNumber * this.pictureNumber);
            } else {
                // Filter the data based on the selected duty value
                return this.storedData.filter(member => member.duty_slugs.includes(filterValue)).slice(0, this.rowNumber * this.pictureNumber);
            }
        },
        // Load more crew members data
        loadMore() {
            this.getData(); // Fetch more data
            this.filterPhotoRow(this.filterValue); // Filter the newly fetched data
        }
    },
    // Fetch initial data and apply initial filtering when the component is created
    async created() {
        await this.getData(); // Fetch initial data
        this.filterPhotoRow(this.filterValue); // Filter initial data
    }
};

</script>
<style lang="scss" scoped>
.action-container {
    background-color: #181818;
}

.title-container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    background-color: #181818;
    height: 25vh;
    color: #fff;

    .title {

        h2,
        p {
            text-transform: uppercase;
            margin-left: 4vw;
        }

        h2 {
            font-size: 60px;
            margin-bottom: 1vw;
        }

        p {
            font-size: 24px;
        }
    }

    .filters {
        text-transform: uppercase;
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        align-items: center;
        width: 45%;

        p {
            cursor: pointer;
            font-weight: 700;
            transition: color 0.2s;
            margin-right: -18vw;
        }

        p:hover {
            color: #C4132F;
        }
    }
}

.pictures {
    margin-bottom: -0.18vw;
    transition: opacity 0.5s;

    .four-pictures {
        height: 38vh;
        width: 24.8vw;
    }

    .five-pictures {
        height: 33.85vh;
        width: 19.85vw;
    }

    .six-pictures {
        height: 26vh;
        width: 16.5vw;
    }

    .crew-member {
        position: relative;
        display: inline-block;
        margin-top: -0.2vw;

        img {
            position: relative;
            transition: filter 0.5s ease, width 0.5s, height 0.5s;
            filter: grayscale(100%);
        }

        img:hover {
            filter: grayscale(0%);
        }

        img:not(:hover) {
            filter: grayscale(100%);
        }
    }

    .facts {
        z-index: 1;
        position: absolute;
        top: 0;
        left: 0;
        background-color: #fff;
        padding: 10px;
        box-sizing: border-box;
        transition: left 1.3s, opacity 2s, width 0.5s, height 0.5s;

        div {
            height: 50%;
            width: 100%;
            display: flex;
            flex-direction: column;
            padding: 0 1vw 1vw 1vw;
            box-sizing: border-box;

            .name {
                font-weight: 700;
                font-size: 26px;
                color: #C4132F;
                margin-top: 0;
                text-transform: uppercase;
            }

            .quote {
                margin-bottom: 0;
                margin-top: 2vw;
            }
        }
    }

    .crew-member:hover .facts,
    .facts:hover {
        left: 100%;
        opacity: 1;
        z-index: 2;
    }

    .facts:hover~img {
        filter: grayscale(0%);
    }

    .crew-member:not(:hover) .facts {
        left: 0%;
        opacity: 0;
    }

    .crew-member:hover .last-photo {
        left: -100%;
    }

}

.buttons {
    display: flex;
    flex-direction: column;
    background-color: #181818;
    color: #fff;
    height: 42vh;

    .columns {
        width: 100%;
        display: flex;
        justify-content: flex-end;

        span {
            margin-bottom: 1vw;
            margin-right: 2vw;
            margin-top: 1vw;
            cursor: pointer;
            width: 32px;
            text-align: center;
            padding-bottom: 0.7vw;
        }

        .selected {
            border-bottom: 1px solid #C4132F;
        }
    }

    .load {
        display: flex;
        align-items: center;
        justify-content: center;
        margin-top: 10vh;

        button {
            width: 12vw;
            height: 6vh;
            font-size: 16px;
            font-weight: 700;
            transition: color 0.5s, background 0.5s, width 0.5s;
            margin-bottom: 3vw;
        }

        button:hover {
            color: #fff;
            background: #C4132F;
            border: 0;
            cursor: pointer;
            width: 13vw;
        }

        button:not(:hover) {
            color: black;
            background: #fff;
            border: 0;
        }
    }
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
    opacity: 0;
}

@media screen and (max-width: 431px) {
    .title-container {

        .title {

            h2 {
                margin-top: 15vw;
                font-size: 4vw;
            }

            p {
                font-size: 2vw;
            }
        }

        .filters {

            p {
                font-size: 1.5vw;
                margin-right: 2vw;
            }
        }
    }

    .pictures {

        .four-pictures {
            height: 14vh;
        }

        .five-pictures {
            height: 13.85vh;
        }

        .six-pictures {
            height: 9vh;
        }

        .crew-member {
            margin-top: -1vw;
        }

        .facts {

            div {

                .name {
                    font-size: 1vw;
                }

                .quote {
                    font-size: 1vw;
                    margin-top: 1vw;
                }

                p {
                    font-size: 1vw;
                }
            }
        }
    }

    .buttons {
        height: 32vh;

        .columns {

            span {
                font-size: 2vw;
                margin-top: 3vw;
                width: 3vw;
            }
        }

        .load {

            button {
                font-size: 2vw;
                width: 24vw;
                height: 4vh;
            }

            button:hover {
                width: 28vw;
            }
        }
    }
}
</style>