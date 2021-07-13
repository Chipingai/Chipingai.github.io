
<div>
  
</div>



<script>
  
  let option_symbols = ['AAPL', 'GOOGL'];
  base_url = 'https://query1.finance.yahoo.com/v7/finance/options/';
  url = base_url + option_symbols[0];
  
  fetch("https://ansyble.herokuapp.com/cors/", {headers: {'Target-URL':url}, cache:'no-cache'}).then(function(response) {
    return response.json();
  }).then(function(data) {
    console.log(data);
  });
  
</script>
