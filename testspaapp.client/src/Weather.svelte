<script>
    let { date, temperatureC, temperatureF, summary } = $props();
</script>

<div class="card">
  <div class="date">{date}</div>
  <div class="temps">{temperatureC}°C / {temperatureF}°F</div>
  <div class="summary">{summary}</div>
</div >

<style>
  .card {
    background: #f9f9f9;
    border-radius: 12px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    padding: 1rem;
    margin: 0.5rem 0;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    max-width: 300px;
  }

  .date {
    font-weight: bold;
    font-size: 1.1rem;
    color: #333;
  }

  .temps {
    font-size: 0.95rem;
    color: #555;
  }

  .summary {
    font-style: italic;
    color: #777;
  }
</style>
