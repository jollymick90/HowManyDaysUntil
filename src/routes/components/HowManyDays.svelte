<script lang="ts">
  const dataPickerFormat = (date: Date): string => {
    return `${date.toISOString().split("T")[0]}`;
  };

  const ONE_DAY_MILLIS = 24 * 60 * 60 * 1000;
  const currentDay = new Date();
  const nextDay = new Date(currentDay.getTime() + ONE_DAY_MILLIS);

  let result = "";
  let dateFrom = dataPickerFormat(currentDay);
  let dateTo = dataPickerFormat(nextDay);

  const calcola = () => {
    const newDateFrom = new Date(dateFrom);
    const newDateTo = new Date(dateTo);

    const delta = newDateTo.getTime() - newDateFrom.getTime();
    const deltaDaysFormat = delta / ONE_DAY_MILLIS;
    result = `la differenza è di ${deltaDaysFormat}`;
  };
</script>

<div>
  ciao
  <label for="start">Start date:</label>

  <input type="date" id="start" name="trip-start" bind:value={dateFrom} />

  <label for="start">From date:</label>

  <input type="date" id="end" name="trip-end" bind:value={dateTo} />

  <button on:click={() => calcola()}> calcola </button>
  <div>
    risultato
    <p>{result}</p>
  </div>
</div>
