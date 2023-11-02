<template>
    <div class="modal">
        <div class="image-block">
            <img @click="$emit('closeModal')" class="close-img" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOEAAADhCAMAAAAJbSJIAAAAM1BMVEX///8AAACjo6OmpqahoaFqamr29vbj4+NtbW2ZmZm9vb12dnaenp63t7d8fHxGRkYfHx/YDSedAAACiUlEQVR4nO3cC1bDIBCFYal9pbWP/a9WK6dqEtIkMLXMzf8tYM6MDEITwtsbAAAAAAAAAAAAAAAAAAAAAAAAAAD4f7tmvzmetqYxt6fjZt/sTGNmO4dv14NhzMM1Bj0bxsx2CXdrs5jrn5gXs5jZzuHXyijm6k/Ml4/iLgTzEletmK+ei00wL7FdYGgMQpbYt9MJH8UR152Ie4MsS2w6+RSP4ns34MYkz3zHbkKFJa568Y5GmeY69TIqWjT6BYaTWa55tlfLErtz8MvVdq+U4dBPKrtREyMYLHdKmRJ/98wSUwXa7ZMK9P77hbxFI1Wg1S6pUKrE+anZRHkSi+SqLtBiLlq1+tOUJljxHLwra7LKWzQqGYVUgVUsE235q1m162BXbqu5aNEoL1VHBebNxeqXibb56TpYJtrmtpyrFo3mpeywwHlt52Qd7Jqetrs5eDe19Vy2aDRtbJy2aDQlebctGo03oOMWjcYKcF/gWBM626qlPSrC+Ry8G25EgRaNhgqRKXCoGV2vg12pYnovHP2O4E2qRKkC040q06LR+Ci6HsGbsRLdFzhWokCBj+eiu61a2vAoSozgzVCJMgUOlShUYP9w2M2rDzuZkh9D+Xko/79Ufj2U39PI70vlf1vI/z6U/40v/5xG/lmb/PNS+Wfe8u8t5N89yb8/lH8HLP8eX/4shvx5GvkzUaXn2qpfNOTPJsqfL5U/Iyx/zlv+rL789xby38zIf/ck/+1a6ShUv2jIf0Mq/x2wTYtVXGKqQKnv8e3uVKh00ZC/F0P/bhP9+2n07xjSvydK/64v/fva9O/c0783cQF3Xy7g/tIF3EELAAAAAAAAAAAAAAAAAAAAAAAAAMDCfAJZehPwT3+hZAAAAABJRU5ErkJggg==" alt="">
            <img :src="modalInfo.image" alt="#">
        </div>
        <div class="text-content">
            <h3>{{ modalInfo.name }}</h3>
            <p>{{ modalInfo.text }}</p>

            <div class="btns">
                <button class="buy">Buy</button>
                <button class="close" @click="$emit('closeModal')">Close</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        modalInfo: {
            type: [String, Object]
        }
    }
}
</script>

<style lang="scss" scoped>
.modal {
    width: 800px;
    height: 500px;
    background: white;
    display: flex;
    align-items: flex-start;
    text-align: center;
    gap: 50px;
    padding: 25px;
    border-radius: 15px;
    margin: 0 auto;
    overflow: hidden;

    .close-img {
        width: 50px;
        height: 50px;
        display: flex;
        margin-top: -10px;
        cursor: pointer;
    }

    img {
        width: 400px;
        height: 400px;
        object-fit: cover;
    }

    .text-content {
        margin-top: 50px;

        h3 {
            text-align: left;
            font-size: 35px;
            margin: 10px 0;
        }

        p {
            text-align: left;
        }

        .btns {
            display: flex;
            align-items: center;
            justify-content: flex-start;
            gap: 5px;
            margin-top: 50px;

            button {
                padding: 10px 25px;
                color: white;
                border-radius: 15px;
                font-size: 22px;
            }

            button.buy {
                background: dodgerblue;
            }

            button.close {
                background: red;
            }
        }
    }
}
</style>