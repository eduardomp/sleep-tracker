<script>
  import Icon from "svelte-awesome";
  import { cloudUpload, areaChart, calendar, fileExcelO } from "svelte-awesome/icons";
  import Datepicker from "svelte-calendar";
  import dayjs from "dayjs";
  import Forms from "./components/Forms.svelte"
  import Modal from 'svelte-simple-modal';

  import { afterUpdate } from 'svelte';

  afterUpdate(() => {
    let calendarPopover = document.querySelector('.sc-popover'); 
    calendarPopover.style.position='unset';
  });

  const daysOfWeek = [
    ["Domingo", "Dom"],
    ["Segunda", "Seg"],
    ["Terça", "Ter"],
    ["Quarta", "Qua"],
    ["Quinta", "Qui"],
    ["Sexta", "Sex"],
    ["Sábado", "Sáb"]
  ];
  const monthsOfYear = [
    ["Janeiro", "Jan"],
    ["Fevereiro", "Fev"],
    ["Março", "Mar"],
    ["Abril", "Abr"],
    ["Maio", "Mai"],
    ["Junho", "Jun"],
    ["Julho", "Jul"],
    ["Agosto", "Ago"],
    ["Setembro", "Set"],
    ["Outubro", "Out"],
    ["Novembro", "Nov"],
    ["Dezembro", "Dez"]
  ];
  



  let dateChosen = null;
  $: selected = new Date();
  $: formatedDate = dayjs(selected).format('DD/MM/YYYY');
</script>

<style>
  .container {
    display: flex;
    color: #9544eb;
  }

  .panel {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #313040a8;
    margin: 10px;
    text-align: center;
    line-height: 40px;
    font-size: 12pt;
    font-weight: bold;
  }

  .btn-datepicker {
    color: #9544eb;
    border: 0;
    background-color: #313040a8;
    margin: 0 0 10% 0;
  }

  .opacity-100 {
    opacity: 1;
  }

  .opacity-90 {
    opacity: 0.9;
  }

  .wd-100 {
    width: 100%;
  }

  .wd-70 {
    width: 70%;
  }

  .wd-50 {
    width: 50%;
  }

  .wd-25 {
    width: 25%;
  }

  .vh-75 {
    height: 75vh;
    overflow: hidden;
  }

  .vh-25 {
    height: 25vh;
    overflow: hidden;
  }

</style>

<main>
  <div class="container vh-75">
    <div class="panel wd-100" >
     
      <Forms selectedDate={ formatedDate }/>

    </div>
  </div>
  <div class="container opacity-90 vh-25">
    <div class="panel wd-100">
      <div class="wd-25">
        <Datepicker
          format={date => dayjs(date).format('DD/MM/YYYY')}
          buttonBackgroundColor="#e20074"
          buttonTextColor="white"
          highlightColor="#e20074"
          dayBackgroundColor="#efefef"
          dayTextColor="#333"
          dayHighlightedBackgroundColor="#e20074"
          dayHighlightedTextColor="#fff"
          {daysOfWeek}
          {monthsOfYear}
          bind:dateChosen
          bind:selected >
              <Icon data={calendar} scale="5"/>
          </Datepicker>
      </div>
      <div class="wd-25">
        <Icon data={cloudUpload} scale="5"/>
      </div>
      <div class="wd-25">
        <Icon data={fileExcelO} scale="5"/>
      </div>
      <div class="wd-25">
        <Icon data={areaChart} scale="5" />
      </div>
    </div>
  </div>

</main>
