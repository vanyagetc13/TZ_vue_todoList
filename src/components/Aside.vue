<template>
    <aside class="aside">
        <header class="header">
            <div class="logo">
                <div class="wrapper"><img src="../assets/logo.svg" alt="logo"></div>

                <h2 class="title">Tasks Book</h2>
            </div>
        </header>
        <nav class="nav">
            <div class="categories">
                <h3>Категории</h3>
                <ul>
                    <li>Дом</li>
                    <li>Семья</li>
                    <li>Работа</li>
                    <li>Спорт</li>
                    <li>Добавить</li>
                </ul>
            </div>
            <div class="data">
                <h3>Данные</h3>
                <ul>
                    <li>Статистика</li>
                    <li>Сравнить</li>
                </ul>
            </div>
        </nav>
        <footer class="exit_wrapper">
            <button>Выйти</button>
        </footer>
    </aside>
</template>

<script lang="ts">
export default {
}
</script>
<style lang="scss" scoped>
.aside {
    padding: 20px 0 20px 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: calc(16%);

    filter: drop-shadow(0px 10px 25px rgba(29, 52, 54, 0.08));

    background-color: #FFF;
    position: fixed;
    left: 0;
    top: 0;
    bottom: 0;
}

.logo {
    display: flex;
    gap: 10px;
    align-items: center;

    .wrapper {
        padding: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #29A19C;

        border-radius: 12px;

        img {
            color: #FFF;
        }
    }

    .title {
        width: min-content;
        color: #29A19C;

        font-size: 1.3em;
        font-weight: 600;
    }
}

.nav {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 60px;
    h3 {
        font-size: 1.7em;
        color: #29A19C;
        margin-bottom: 20px;
    }

    ul {
        list-style-type: none;
        font-size: 1.14em;

        li {
            cursor: pointer;
        }

        li + li {
            margin-top: 30px;
        }
    }
}

.exit_wrapper {
    margin-top: 200px;

    button {
        border: none;
        padding: 5px 10px;
        background: transparent;
        font-size: 1.14em;
    }
}
</style>