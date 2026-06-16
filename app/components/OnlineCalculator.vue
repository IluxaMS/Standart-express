<template>
    <section class="calculator-section">
        <img src="/public/background_decor_2.png" alt="" class="bg-decor bg-decor--bottom">
        <img src="../public/decor-white-bottom.png" alt="" class="decor_mob decor--black-bottom" />
        <img src="../public/decor-orange-top.png" alt="" class="decor_mob decor--orange-top" />
        <img src="../public/decor-loader-left.png" alt="" class="decor_mob decor--loader-left" />
        <img src="../public/decor-truck-right2.png" alt="" class="decor_mob decor--truck-right" />

        <div class="calculator-container">
            <div class="calculator-header">
                <h2 class="calculator-title">ОНЛАЙН КАЛЬКУЛЯТОР</h2>
                <p class="calculator-subtitle">
                    Введите данные для предварительного<br class="br_mob">
                    расчета стоимости заказа услуги<br class="br_mob">
                    «Грузчики» и получите скидку<br class="br_mob">
                    <span class="highlight-badge">до 10%</span> на первый заказ.
                </p>
            </div>

            <div class="calculator-tabs">
                <button v-for="tab in tabs" :key="tab.id" class="tab-btn"
                    :class="{ 'tab-btn--active': activeTab === tab.id }" @click="activeTab = tab.id">
                    {{ tab.label }}
                </button>
            </div>

            <form class="calculator-form" @submit.prevent="calculateCost">

                <div class="form-row">

                    <div v-if="activeTab === 'loaders'" class="input-card input-card--large">
                        <span class="card-label">Кол-во грузчиков</span>
                        <div class="counter-wrapper">
                            <img src="/public/icon_loader.png" alt="icon" class="card-icon">
                            <span class="counter-value">{{ counters.primary }}</span>
                            <div class="counter-controls">
                                <button type="button" @click="counters.primary++"><img src="/public/plus.png"
                                        alt="+"></button>
                                <button type="button" @click="counters.primary > 1 && counters.primary--"><img
                                        src="/public/minus.png" alt="-"></button>
                            </div>
                        </div>
                    </div>

                    <div v-if="activeTab === 'rigging'" class="input-card input-card--large">
                        <span class="card-label">Вес груза в тоннах</span>
                        <div class="counter-wrapper">
                            <img src="/public/icon_weight.png" alt="icon" class="card-icon">
                            <span class="counter-value">{{ counters.primary }}</span>
                            <div class="counter-controls">
                                <button type="button" @click="counters.primary++"><img src="/public/plus.png"
                                        alt="+"></button>
                                <button type="button" @click="counters.primary > 1 && counters.primary--"><img
                                        src="/public/minus.png" alt="-"></button>
                            </div>
                        </div>
                    </div>

                    <div v-if="['moving', 'handymen'].includes(activeTab)" class="input-card input-card--large">
                        <span class="card-label">{{ activeTab === 'handymen' ? 'Кол-во рабочих' : 'Грузчики' }}</span>
                        <div class="counter-wrapper">
                            <img src="/public/icon_loader.png" alt="icon" class="card-icon">
                            <span class="counter-value">{{ counters.primary }}</span>
                            <div class="counter-controls">
                                <button type="button" @click="counters.primary++"><img src="/public/plus.png"
                                        alt="+"></button>
                                <button type="button" @click="counters.primary > 1 && counters.primary--"><img
                                        src="/public/minus.png" alt="-"></button>
                            </div>
                        </div>
                    </div>

                    <div class="input-card input-card--large date-input-wrapper">
                        <span class="card-label">Дата/время</span>
                        <div class="date-wrapper" @click="openCalendar">
                            <img src="/public/calendar_icon.png" alt="calendar" class="card-icon calendar-trigger">
                            <span class="date-display">{{ formattedDateRange }}</span>
                        </div>
                    </div>

                    <div v-if="activeTab !== 'rigging'" class="input-card input-card--large input-card--large_last">
                        <span class="card-label">Кол-во часов</span>
                        <div class="counter-wrapper">
                            <img src="/public/clock_icon.png" alt="clock" class="card-icon">
                            <span class="counter-value">{{ counters.hours }}</span>
                            <div class="counter-controls">
                                <button type="button" @click="counters.hours++"><img src="/public/plus.png"
                                        alt="+"></button>
                                <button type="button" @click="counters.hours > 1 && counters.hours--"><img
                                        src="/public/minus.png" alt="-"></button>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div v-if="activeTab === 'moving'" class="input-card input-card--medium dropdown-container_3">
                        <div class="dropdown-trigger">
                            <img src="/public/services.png" alt="services" class="card-icon">
                            <span>Дополнительные услуги</span>
                            <span class="badge-count">4</span>
                        </div>
                    </div>

                    <div v-if="['handymen', 'moving'].includes(activeTab)"
                        class="input-card input-card--medium dropdown-container dropdown-container_4"
                        :class="{ 'dropdown-open': openDropdown === 'workType' }">
                        <div class="dropdown-trigger" @click="toggleDropdown('workType')">
                            <img src="/public/services.png" alt="work" class="card-icon">
                            <span>{{ formData.workType || 'Тип работ' }}</span>
                            <img src="/public/dropdown-arrow_icon.png" alt="arrow" class="dropdown-arrow">
                        </div>
                        <ul v-if="openDropdown === 'workType'" class="dropdown-list">
                            <li v-for="item in workTypeOptions" :key="item" @click="selectOption('workType', item)">{{
                                item }}</li>
                        </ul>
                    </div>

                    <div v-if="['loaders', 'handymen'].includes(activeTab)"
                        class="checkbox-row offset-medium outside-the-city">
                        <label class="custom-checkbox">
                            <input type="checkbox" v-model="formData.outsideCity">
                            <span class="checkmark"></span>
                            За городом
                        </label>
                    </div>

                    <div v-if="activeTab === 'rigging'"
                        class="input-card input-card--medium dropdown-container dropdown-container_2"
                        :class="{ 'dropdown-open': openDropdown === 'riggingWork' }">
                        <div class="dropdown-trigger" @click="toggleDropdown('riggingWork')">
                            <img src="/public/services.png" alt="work" class="card-icon">
                            <span>{{ formData.riggingWork || 'Вид работ' }}</span>
                            <img src="/public/dropdown-arrow_icon.png" alt="arrow" class="dropdown-arrow">
                        </div>
                        <ul v-if="openDropdown === 'riggingWork'" class="dropdown-list">
                            <li v-for="item in riggingWorkOptions" :key="item"
                                @click="selectOption('riggingWork', item)">{{ item }}</li>
                        </ul>
                    </div>

                    <div v-if="activeTab === 'rigging'" class="input-card input-card--medium dropdown-container"
                        :class="{ 'dropdown-open': openDropdown === 'techType' }">
                        <div class="dropdown-trigger" @click="toggleDropdown('techType')">
                            <img src="/public/tech_icon.png" alt="tech" class="card-icon">
                            <span>{{ formData.techType || 'Вид техники' }}</span>
                            <img src="/public/dropdown-arrow_icon.png" alt="arrow" class="dropdown-arrow">
                        </div>
                        <ul v-if="openDropdown === 'techType'" class="dropdown-list">
                            <li v-for="item in techTypeOptions" :key="item" @click="selectOption('techType', item)">{{
                                item }}</li>
                        </ul>
                    </div>

                    <div v-if="activeTab === 'moving'"
                        class="input-card input-card--medium dropdown-container car-dropdown"
                        :class="{ 'dropdown-open': openDropdown === 'car' }">
                        <div class="dropdown-trigger" @click="toggleDropdown('car')">
                            <img src="/public/tech_icon.png" alt="car" class="card-icon">
                            <span>{{ formData.car || 'Выберите автомобиль' }}</span>
                            <img src="/public/dropdown-arrow_icon.png" alt="arrow" class="dropdown-arrow">
                        </div>
                        <ul v-if="openDropdown === 'car'" class="dropdown-list car-list">
                            <li v-for="(car, index) in carOptions" :key="index" @click="selectOption('car', car)"
                                :class="{ 'selected': formData.car === car }">{{ car }}</li>
                        </ul>
                    </div>

                    <div v-if="activeTab === 'rigging'" class="checkbox-row offset-large_1">
                        <label class="custom-checkbox custom-checkbox_2">
                            <input type="checkbox" v-model="formData.transportRequired">
                            <span class="checkmark"></span>
                            Требуется транспортировка
                        </label>
                    </div>
                </div>

                <div v-if="activeTab === 'moving'" class="checkbox-row offset-large_2">
                    <label class="custom-checkbox">
                        <input type="checkbox" v-model="formData.intercity">
                        <span class="checkmark"></span>
                        Межгород
                    </label>
                </div>

                <div class="form-row contact-row">
                    <div class="input-wrapper">
                        <input type="text" placeholder="Имя" v-model="formData.name" @input="validateName"
                            :class="{ 'input-error': errors.name }" class="contact-input">
                        <span v-if="errors.name" class="error-text">Ошибка</span>
                    </div>

                    <div class="input-wrapper">
                        <input type="tel" placeholder="+7" v-model="formData.phone" @input="validatePhone"
                            :class="{ 'input-error': errors.phone }" class="contact-input">
                        <span v-if="errors.phone" class="error-text">Ошибка</span>
                    </div>

                    <button type="submit" class="calc-submit-btn">
                        <img src="/public/calc_icon.png" alt="calc" class="btn-icon">
                        Рассчитать стоимость
                    </button>
                </div>
            </form>
        </div>

        <div v-if="isCalendarOpen" class="calendar-modal-overlay" @click.self="closeCalendar">
            <div class="calendar-modal">
                <div class="calendar-months">

                    <div class="month-block">
                        <div class="month-header">
                            <button class="nav-btn nav-btn--left" @click="changeLeftMonth(-1)">
                                <img src="/public/dropdown-arrow_icon.png" alt="<">
                            </button>
                            <span class="month-name">{{ getMonthName(calendarDateLeft.getMonth()) }} {{
                                calendarDateLeft.getFullYear() }}</span>
                            <button class="nav-btn nav-btn--right" @click="changeLeftMonth(1)">
                                <img src="/public/dropdown-arrow_icon.png" alt=">">
                            </button>
                        </div>
                        <div class="week-days">
                            <span v-for="d in ['ПН', 'ВТ', 'СР', 'ЧТ', 'ПТ', 'СБ', 'ВС']" :key="d">{{ d }}</span>
                        </div>
                        <div class="days-grid">
                            <span v-for="day in getDaysArray(calendarDateLeft)" :key="day.dateStr" class="day" :class="{
                                'empty': day.isEmpty,
                                'active': isDayActive(day.dateStr),
                                'in-range': isDayInRange(day.dateStr)
                            }" @click="!day.isEmpty && handleDayClick(day.dateStr)">
                                {{ day.dayNum }}
                            </span>
                        </div>
                    </div>

                    <div class="month-block">
                        <div class="month-header">
                            <button class="nav-btn nav-btn--left" @click="changeRightMonth(-1)">
                                <img src="/public/dropdown-arrow_icon.png" alt="<">
                            </button>
                            <span class="month-name">{{ getMonthName(calendarDateRight.getMonth()) }} {{
                                calendarDateRight.getFullYear() }}</span>
                            <button class="nav-btn nav-btn--right" @click="changeRightMonth(1)">
                                <img src="/public/dropdown-arrow_icon.png" alt=">">
                            </button>
                        </div>
                        <div class="week-days">
                            <span v-for="d in ['ПН', 'ВТ', 'СР', 'ЧТ', 'ПТ', 'СБ', 'ВС']" :key="d">{{ d }}</span>
                        </div>
                        <div class="days-grid">
                            <span v-for="day in getDaysArray(calendarDateRight)" :key="day.dateStr" class="day" :class="{
                                'empty': day.isEmpty,
                                'active': isDayActive(day.dateStr),
                                'in-range': isDayInRange(day.dateStr)
                            }" @click="!day.isEmpty && handleDayClick(day.dateStr)">
                                {{ day.dayNum }}
                            </span>
                        </div>
                    </div>
                </div>

                <div class="time-picker">
                    <div class="time-group">
                        <label>Часы</label>
                        <input type="number" v-model.number="tempTime.hours" min="0" max="23" class="time-input">
                    </div>
                    <span class="time-separator">:</span>
                    <div class="time-group">
                        <label>Минуты</label>
                        <input type="number" v-model.number="tempTime.minutes" min="0" max="59" class="time-input">
                    </div>
                </div>

                <div class="calendar-footer">
                    <span class="selected-range">{{ formattedDateRange }}</span>
                    <div class="calendar-actions">
                        <button class="btn-cancel" @click="closeCalendar">Отмена</button>
                        <button class="btn-apply" @click="applyDate">Применить</button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref, reactive, computed } from 'vue';

const tabs = [
    { id: 'loaders', label: 'Грузчики' },
    { id: 'rigging', label: 'Такелаж' },
    { id: 'moving', label: 'Переезд' },
    { id: 'handymen', label: 'Разнорабочие' }
];

const activeTab = ref('loaders');
const openDropdown = ref<string | null>(null);
const isCalendarOpen = ref(false);

const counters = reactive({ primary: 2, hours: 10 });

interface FormData {
    date: string;
    outsideCity: boolean;
    transportRequired: boolean;
    intercity: boolean;
    name: string;
    phone: string;
    workType: string;
    riggingWork: string;
    techType: string;
    car: string;
}

const formData = reactive<FormData>({
    date: '',
    outsideCity: false,
    transportRequired: false,
    intercity: false,
    name: '',
    phone: '+7',
    workType: '',
    riggingWork: '',
    techType: '',
    car: ''
});

const errors = reactive({ name: false, phone: false });

const workTypeOptions = ['Подъем на этаж', 'Спуск с этажа', 'Такелажные работы', 'Уборка'];
const riggingWorkOptions = ['Демонтаж оборудования', 'Монтаж станков', 'Перемещение сейфов'];
const techTypeOptions = ['Автокран 25т', 'Манипулятор 10т', 'Гидроборт'];
const carOptions = ['Газель 3 метра 1,5 тонны', 'Газель 4 метра до 2 тонн', 'Газель 5 метров до 2 тонн', 'Газель 7 метров 5 тонн', 'Фура 12 метров 20 тонн'];

const startDate = ref<string | null>(null);
const endDate = ref<string | null>(null);

const calendarDateLeft = ref(new Date());
const calendarDateRight = ref(new Date());

const tempTime = reactive({ hours: 12, minutes: 0 });

const formattedDateRange = computed(() => {
    if (!startDate.value) return 'Выберите дату';

    const format = (iso: string) => {
        const d = new Date(iso);
        return `${String(d.getDate()).padStart(2, '0')}/${String(d.getMonth() + 1).padStart(2, '0')}/${d.getFullYear()}`;
    };

    let result = format(startDate.value);
    if (endDate.value) {
        result += ` - ${format(endDate.value)}`;
    }

    const h = String(tempTime.hours).padStart(2, '0');
    const m = String(tempTime.minutes).padStart(2, '0');
    result += `, ${h}:${m}`;

    return result;
});

const validateName = () => {
    const regex = /^[a-zA-Zа-яА-Я\s]*$/;
    errors.name = !regex.test(formData.name) && formData.name.length > 0;
};

const validatePhone = () => {
    errors.phone = /[a-zA-Zа-яА-Я]/.test(formData.phone);
};

const toggleDropdown = (name: string) => {
    openDropdown.value = openDropdown.value === name ? null : name;
};

const selectOption = (field: keyof FormData, value: string) => {
    (formData[field] as string) = value;
    openDropdown.value = null;
};

const calculateCost = () => {
    if (!errors.name && !errors.phone) alert('Расчет отправлен!');
};

const getMonthName = (monthIndex: number) => {
    const months = ['Январь', 'Февраль', 'Март', 'Апрель', 'Май', 'Июнь', 'Июль', 'Август', 'Сентябрь', 'Октябрь', 'Ноябрь', 'Декабрь'];
    return months[monthIndex];
};

const getDaysArray = (date: Date) => {
    const year = date.getFullYear();
    const month = date.getMonth();
    const firstDay = new Date(year, month, 1).getDay();
    const daysInMonth = new Date(year, month + 1, 0).getDate();
    const startOffset = firstDay === 0 ? 6 : firstDay - 1;

    const days = [];
    for (let i = 0; i < startOffset; i++) days.push({ dayNum: '', isEmpty: true, dateStr: '' });
    for (let i = 1; i <= daysInMonth; i++) {
        const d = new Date(year, month, i);
        const iso = d.toISOString().slice(0, 10);
        days.push({ dayNum: i, isEmpty: false, dateStr: iso });
    }
    return days;
};

const isDayActive = (dateStr: string) => {
    return dateStr === startDate.value || dateStr === endDate.value;
};

const isDayInRange = (dateStr: string) => {
    if (!startDate.value || !endDate.value) return false;
    return dateStr > startDate.value && dateStr < endDate.value;
};

const handleDayClick = (dateStr: string) => {
    if (!startDate.value || (startDate.value && endDate.value)) {
        startDate.value = dateStr;
        endDate.value = null;
    } else if (startDate.value && !endDate.value) {
        if (dateStr < startDate.value) {
            endDate.value = startDate.value;
            startDate.value = dateStr;
        } else {
            endDate.value = dateStr;
        }
    }
};

const changeLeftMonth = (delta: number) => {
    const d = new Date(calendarDateLeft.value.getTime());
    d.setMonth(d.getMonth() + delta);
    calendarDateLeft.value = d;
};

const changeRightMonth = (delta: number) => {
    const d = new Date(calendarDateRight.value.getTime());
    d.setMonth(d.getMonth() + delta);
    calendarDateRight.value = d;
};

const openCalendar = () => {
    calendarDateLeft.value = new Date();
    calendarDateRight.value = new Date();
    calendarDateRight.value.setMonth(calendarDateRight.value.getMonth() + 1);

    tempTime.hours = 12;
    tempTime.minutes = 0;
    isCalendarOpen.value = true;
};

const closeCalendar = () => {
    isCalendarOpen.value = false;
};

const applyDate = () => {
    if (startDate.value) {
        const start = new Date(startDate.value);
        start.setHours(tempTime.hours, tempTime.minutes);

        let endStr = '';
        if (endDate.value) {
            const end = new Date(endDate.value);
            end.setHours(tempTime.hours, tempTime.minutes);
            endStr = end.toISOString();
        }

        formData.date = `${start.toISOString()}|${endStr}`;
    }
    closeCalendar();
};

if (typeof window !== 'undefined') {
    window.addEventListener('click', (e: any) => {
        if (!e.target.closest('.dropdown-container')) openDropdown.value = null;
    });
}
</script>

<style scoped lang="scss">
.calculator-section {
    position: relative;
    width: 100%;
    min-height: 750px;
    background-color: #1A1A1A;
    padding: 60px 0;
    overflow: hidden;
    color: #FFFFFF;
    font-family: "Euclid Circular A", sans-serif;
}

.bg-decor {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    pointer-events: none;
    z-index: 0;
}

.bg-decor--bottom {
    z-index: 0;
}

.bg-decor--top {
    z-index: 1;
}

.calculator-container {
    position: relative;
    z-index: 2;
    max-width: 1250px;
    margin: 0 auto;
    padding: 0 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-family: "Euclid Circular A", sans-serif;
}

.calculator-header {
    text-align: center;
    margin-bottom: 40px;
}

.calculator-title {
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    text-transform: uppercase;
    margin: 0 0 20px 0;
}

.calculator-subtitle {
    font-weight: 300;
    font-size: 20px;
    line-height: 160%;
    margin: 0;
}

.highlight-badge {
    background-color: #ED9121;
    color: #FFFFFF;
    font-weight: 700;
    padding: 2px 10px;
    border-radius: 20px;
    display: inline-block;
}

.calculator-tabs {
    display: flex;
    gap: 30px;
    margin-bottom: 30px;
}

.tab-btn {
    background: none;
    border: none;
    color: #FFFFFF;
    font-size: 18px;
    font-weight: 500;
    cursor: pointer;
    padding-bottom: 5px;
    transition: all 0.3s;
    border-bottom: 1px dashed rgba(255, 255, 255, 0.5);

    &:hover {
        color: #ED9121;
    }

    &--active {
        color: #ED9121;
        border-bottom: none;
        font-weight: 500;
    }
}

.form-row {
    display: flex;
    gap: 20px;
    width: 100%;
    justify-content: flex-start;
    flex-wrap: wrap;
    margin-top: 27px;
}

.input-card {
    background: #FFFFFF;
    border-radius: 20px;
    color: #000000;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 0 25px;
    box-sizing: border-box;
    margin-bottom: 10px;

    &--large {
        width: 386px;
        height: 100px;
    }

    &--medium {
        width: 386px;
        height: 70px;
    }
}

.card-label {
    font-size: 13px;
    color: #000;
    font-weight: 400;
    opacity: 60%;
}

.counter-wrapper {
    display: flex;
    align-items: center;
    gap: 15px;
}

.card-icon {
    width: 24px;
    height: 24px;
    object-fit: contain;
}

.counter-value {
    font-size: 16px;
    font-weight: 400;
    flex-grow: 1;
}

.counter-controls {
    display: flex;
    flex-direction: column;
    gap: 15px;
    align-items: center;
    margin-bottom: 10px;
}

.counter-controls button {
    background: none;
    border: none;
    cursor: pointer;
    padding: 0;

    img {
        width: 20px;
        height: 20px;
        display: block;
    }
}

.date-wrapper {
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    margin-top: 20px;
    margin-bottom: 20px;
}

.calendar-trigger {
    cursor: pointer;
}

.date-display {
    font-size: 16px;
    font-weight: 500;
    color: #000;
}

.dropdown-trigger {
    display: flex;
    align-items: center;
    gap: 10px;
    height: 100%;
    font-size: 16px;
    font-weight: 500;
    cursor: pointer;
    position: relative;
}

.badge-count {
    margin-left: auto;
    background: #ED9121;
    color: #fff;
    width: 24px;
    height: 24px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 12px;
    font-weight: 700;
}

.dropdown-arrow {
    margin-left: auto;
    width: 25px;
    transition: transform 0.3s;
}

.dropdown-container {
    position: relative;
}

.dropdown-list {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: #FFFFFF;
    border-radius: 20px;
    list-style: none;
    padding: 10px 0;
    margin: 0;
    z-index: 10;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);

    li {
        padding: 10px 25px;
        cursor: pointer;
        font-size: 16px;
        color: #000;

        &:hover {
            border-radius: 10px;
            background-color: #ED9121;
        }
    }
}

.car-list li.selected {
    color: #ED9121;
    font-weight: 700;
}

.checkbox-row {
    display: flex;
    align-items: center;
    margin-top: 4px;
}

.offset-large_1 {
    justify-content: end;
}

.offset-medium {
    width: 100%;
    margin-top: -4px;
}

.offset-large_2 {
    margin-top: 26px;
}

.outside-the-city {
    margin-top: 5px;
}

.centered-checkbox {
    width: 100%;
    justify-content: center;
    margin-top: 20px;
}

.custom-checkbox {
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    font-size: 14px;
    user-select: none;

    input {
        display: none;
    }

    .checkmark {
        width: 20px;
        height: 20px;
        background: transparent;
        border: 2px solid #E0E0E0;
        border-radius: 4px;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all 0.2s;

        &::after {
            content: '';
            width: 6px;
            height: 10px;
            border: solid white;
            border-width: 0 2px 2px 0;
            transform: rotate(45deg) scale(0);
            transition: transform 0.2s;
        }
    }

    input:checked+.checkmark {
        background: #ED9121;
        border-color: #ED9121;

        &::after {
            transform: rotate(45deg) scale(1);
        }
    }
}

.contact-row {
    margin-top: 40px;
}

.input-wrapper {
    position: relative;
    width: 387px;
}

.contact-input {
    width: 100%;
    height: 60px;
    border-radius: 30px;
    border: 2px solid #ffffff;
    padding: 0 25px;
    font-size: 16px;
    font-family: inherit;
    outline: none;
    box-sizing: border-box;
    transition: border-color 0.3s;

    &:focus {
        border-color: #ED9121;
    }

    &.input-error {
        border-color: #FF0000;
    }
}

.error-text {
    position: absolute;
    bottom: -20px;
    left: 25px;
    color: #FF0000;
    font-size: 12px;
}

.calc-submit-btn {
    width: 387px;
    height: 60px;
    border-radius: 30px;
    background: #ED9121;
    border: none;
    color: #FFFFFF;
    font-size: 16px;
    font-weight: 600;
    font-family: inherit;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    transition: filter 0.2s;

    &:hover {
        filter: brightness(1.1);
    }
}

.calendar-modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: center;
}

.calendar-modal {
    background: #FFFFFF;
    border-radius: 20px;
    padding: 25px;
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.2);
    width: 700px;
}

.calendar-months {
    display: flex;
    gap: 30px;
    margin-bottom: 20px;
}

.month-block {
    flex: 1;
}

.month-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-weight: 700;
    margin-bottom: 15px;
    font-size: 16px;
    color: #000;
}

.nav-btn {
    background: none;
    border: none;
    cursor: pointer;
    padding: 5px;
    display: flex;
    align-items: center;
    justify-content: center;

    img {
        width: 12px;
        height: 12px;
        object-fit: contain;
    }
}

.nav-btn--left img {
    transform: rotate(90deg);
}

.nav-btn--right img {
    transform: rotate(-90deg);
}

.week-days {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    text-align: center;
    color: #000;
    font-size: 12px;
    margin-bottom: 10px;
    font-weight: 500;
}

.days-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 5px;
}

.day {
    aspect-ratio: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    font-size: 14px;
    cursor: pointer;
    color: #000;
    transition: all 0.2s;

    &.empty {
        visibility: hidden;
        pointer-events: none;
    }

    &.active {
        background-color: #ED9121;
        color: #FFFFFF;
        font-weight: 700;
    }

    &.in-range {
        background-color: rgba(237, 145, 33, 0.15);
        border-radius: 0;
        color: #000;
    }

    &:not(.empty):not(.active):hover {
        background-color: #F5F5F5;
    }
}

.time-picker {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 15px;
    margin: 20px 0;
    padding: 15px 0;
    border-top: 1px solid #F0F0F0;
    border-bottom: 1px solid #F0F0F0;
}

.time-group {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 5px;
}

.time-group label {
    font-size: 12px;
    color: #888;
    font-weight: 500;
}

.time-input {
    width: 60px;
    height: 36px;
    text-align: center;
    border: 1px solid #E0E0E0;
    border-radius: 8px;
    font-size: 16px;
    font-family: inherit;
    color: #000;

    &:focus {
        outline: none;
        border-color: #ED9121;
    }
}

.time-separator {
    font-size: 24px;
    font-weight: bold;
    color: #000;
    margin-top: 10px;
}

.calendar-footer {
    display: flex;
    justify-content: end;
    align-items: center;
    padding-top: 10px;
}

.selected-range {
    font-size: 14px;
    color: #000;
    font-weight: 500;
    margin-right: 15px;
}

.calendar-actions {
    display: flex;
    gap: 4px;
}

.btn-cancel,
.btn-apply {
    padding: 12px 24px;
    border-radius: 30px;
    border: none;
    font-weight: 600;
    cursor: pointer;
    font-size: 14px;
    transition: all 0.2s;
}

.btn-cancel {
    background: #F5F5F5;
    color: #000;

    &:hover {
        background: #E0E0E0;
    }
}

.btn-apply {
    background: #ED9121;
    color: #FFFFFF;

    &:hover {
        filter: brightness(1.1);
    }
}

.decor--black-bottom {
    position: absolute;
    left: 7%;
    bottom: 0;
    width: 70px;
    height: 205px;
    z-index: 3;
}

.decor--orange-top {
    position: absolute;
    right: 8%;
    top: 0;
    width: 70px;
    height: auto;
    z-index: 3;
}

.decor--loader-left {
    position: absolute;
    left: 0;
    bottom: 68%;
    width: 232px;
    height: 81px;
    z-index: 3;
}

.decor--truck-right {
    position: absolute;
    right: 0;
    top: 72%;
    width: 151px;
    height: 47px;
    z-index: 3;
}

.br_mob {
    display: none;
}

@media (max-width: 1300px) {
    .calculator-tabs {
        gap: 24px;
    }

    .tab-btn {
        font-size: 16px;
    }

    .calculator-title {
        font-size: 26px;
    }

    .calculator-subtitle {
        font-size: 16px;
        max-width: 400px;
    }

    .form-row {
        flex-direction: column;
        align-items: center;
        width: 386px;
        margin-top: 0 !important;
        margin-bottom: 0 !important;
        gap: 12px !important;
    }

    .input-card,
    .input-wrapper,
    .calc-submit-btn {
        width: 100%;
        max-width: 386px;
        margin-bottom: 0 !important;
    }

    .contact-row {
        margin-top: 0 !important;
        gap: 12px !important;
    }

    .offset-large_1,
    .offset-large_2,
    .offset-medium,
    .outside-the-city {
        margin-top: 0 !important;
        display: contents;
    }

    .dropdown-container_2 {
        margin-top: 0 !important;
    }

    .input-card--large_last {
        margin-bottom: 0 !important;
    }

    .custom-checkbox_2 {
        display: none;
    }

    .calendar-modal {
        width: 90%;
        max-width: 600px;
    }

    .calendar-months {
        gap: 10px;
    }

    .outside-the-city,
    .offset-large_2 {
        display: none;
    }

    .contact-row,
    .dropdown-container_2 {
        margin-top: 12px !important;
    }

    .dropdown-container_3 {
        margin-top: 12px !important;
        margin-bottom: -15px !important;
    }

    .dropdown-container_4 {
        margin-top: 12px !important;
    }

    .error-text {
        margin-bottom: 8px;
    }

    .calculator-subtitle br {
        display: block !important;
        content: "";
        margin-bottom: 0;
    }

    .br_desc {
        display: none;
    }

    .br_mob {
        display: block;
    }

    .decor_mob {
        display: none;
    }
}
</style>