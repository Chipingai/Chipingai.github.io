
<div>
  
</div>



<script>
  
  let option_symbols = ['AAPL', 'GOOGL'];
  base_url = 'https://query1.finance.yahoo.com/v7/finance/options/';
  url = base_url + option_symbol[0];
  
  fetch(url, {cache:'no-cache'}).then(function(response) {
    return response.json();
  }).then(function(data) {
    console.log(data);
  });
  
</script>
