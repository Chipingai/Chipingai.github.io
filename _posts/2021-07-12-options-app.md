
<div>
  
</div>



<script>
  
  let working_data = [];
  let option_symbols = ['AAPL', 'GOOGL'];
  let base_url = 'https://query1.finance.yahoo.com/v7/finance/options/';
  
  for (let i = 0; i < option_symbols.length; i++) {
    fetch("https://ansyble.herokuapp.com/cors/", {headers: {'Target-URL':base_url + option_symbols[i]}, cache:'no-cache'}).then(function(response) {
      return response.json();
    }).then(function(data) {
      working_data.push(data.optionChain.result[0]);
      console.log(working_data[i]);
    });
  }
  
  
</script>
