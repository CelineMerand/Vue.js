<template>
  <div class="datepicker__container">
    <input type="text" :value="date_formatted">
    <input type="text" :name="name" :value="date_raw"/>
    <datepickerAgenda v-bind:date="date" name="agenda"></datepickerAgenda>
  </div>
</template>

<script>
  import moment from 'moment';
  import DatepickerAgendaComponent from './Datepicker-agenda';

  moment.locale('fr');

  export default {
    components: {
      datepickerAgenda: DatepickerAgendaComponent
    },
    props: {
      value: {type: String, required: true},
      format: {type: String, default: 'YYYY-MM-DD'},
      name: {type: String}
    },
    data: function () {
      return {
        date: moment(this.value, 'YYYY-MM-DD')
      }
    },
    computed: {
      date_formatted: function () {
        return this.date.format(this.format);
      },
      date_raw: function () {
        return this.date.format('YYYY-MM-DD');
      }
    }
  }
</script>

<style>
  .datepicker__container {
    position: relative;
  }
</style>

