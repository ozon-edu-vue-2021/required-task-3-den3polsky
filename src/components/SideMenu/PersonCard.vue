<template>
    <div class="person">
        <div class="person__photo">
            <img
                :src="person.picture"
                alt="photo"
            />
        </div>
        
        <div class="person__info">
            <div class="person__info-name">
                <b>{{ person.name }} ({{ person.age }})</b>
            </div>

            <div class="person__info-department"  :style="{ '--marker-color': person.department.color }">
                <b>{{person.department.text}}</b>
            </div>

            <div class="person__info-email"><b>Почта:</b> {{ person.email }}</div>
            <div class="person__info-email">
                <b>Дата регистрации:</b> {{ formatedDate }}
            </div>
            <div class="person__info-about"><b>О себе:</b> {{ person.about }}</div>
        </div>
    </div>
</template>

<script>

import {format} from 'date-fns'

export default {
    props: {
        person: {
            type: Object,
            default: null,
        },
    },
    computed: {
        formatedDate() {
            return format(new Date(this.person.registered), 'dd.MM.yyyy');
        },
    },
};
</script>

<style scoped>
.person {
    display: grid;
    grid-template-columns: 50px 1fr;
    grid-gap: 8px;
}

.person__photo img {
    height: 50px;
    width: 50px;
    border-radius: 50%;
}

.person__info {
    display: grid;
    grid-gap: 8px;
}

.person__info-name {
    margin-bottom: 10px;
}

.person__info-department {

    border-bottom: var(--marker-color) 3px solid;
    width: fit-content;
}


</style>
