
<div>
  
</div>



<script>
  
  
  function within_two_weeks(unix_time) {
    let now = Date.now();
    return (unix_time - now/1000 < 16*24*60*60);
  }
  
  let data = {};
                                               
  let expirations = [];
  
  let first_run_data = [];
  let option_symbols = ['AAPL', 'GOOGL'];
  let base_url = 'https://query1.finance.yahoo.com/v7/finance/options/';
  
  for (let i = 0; i < option_symbols.length; i++) {
  
    data[option_symbols[i]] = [];
    fetch("https://ansyble.herokuapp.com/cors/", {headers: {'Target-URL':base_url + option_symbols[i]}, cache:'no-cache'}).then(function(response) {
      return response.json();
    }).then(function(data) {
      data[option_symbols[i]].push(data.optionChain.result[0]);
      console.log(data[option_symbols[i]][0]);
                                            
      let myExpirations = [];
      for (let j = 0; j < data[option_symbols[i]][0].expirationDates.length; j++) {
        if (within_two_weeks(data[option_symbols[i]][0].expirationDates[j])) 
          myExpirations.push(data[option_symbols[i]][0].expirationDates[j]);
      }
      console.log(myExpirations);
      expirations.push(myExpirations);      
    });
  }
  
  
                                                                 
                                                                 
</script>
