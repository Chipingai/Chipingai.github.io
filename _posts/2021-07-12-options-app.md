
<div>
  
</div>



<script>
  
  
  function within_two_weeks(unix_time) {
    let now = Date.now();
    return (unix_time - now < 16*24*60*60*1000;
  }
  
  
  let expirations = [];
  
  let first_run_data = [];
  let option_symbols = ['AAPL', 'GOOGL'];
  let base_url = 'https://query1.finance.yahoo.com/v7/finance/options/';
  
  for (let i = 0; i < option_symbols.length; i++) {
    fetch("https://ansyble.herokuapp.com/cors/", {headers: {'Target-URL':base_url + option_symbols[i]}, cache:'no-cache'}).then(function(response) {
      return response.json();
    }).then(function(data) {
      first_run_data.push(data.optionChain.result[0]);
      console.log(first_run_data[i]);
                                            
      let myExpirations = [];
      for (let j = 0; j < first_run_data[i].expirationDates.length; j++) {
        if (within_two_weeks(first_run_data[i].expirationDates[j])) 
          myExpirations.push(first_run_data[i].expirationDates[j]);
      }
      console.log(myExpirations);
      expirations.push(myExpirations);      
    });
  }
  
  
                                                                 
                                                                 
</script>
