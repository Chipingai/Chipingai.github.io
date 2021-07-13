
<div>
  
</div>



<script>
  
  
  function within_two_weeks(unix_time) {
    let now = Date.now();
    return (unix_time - now/1000 < 16*24*60*60);
  }
  
  var allData = {};
                                               
  var expirations = [];
  var option_symbols = ['AAPL', 'GOOGL'];
  var base_url = 'https://query1.finance.yahoo.com/v7/finance/options/';
  
  for (let i = 0; i < option_symbols.length; i++) {
  
    allData[option_symbols[i]] = [];
    fetch("https://ansyble.herokuapp.com/cors/", {headers: {'Target-URL':base_url + option_symbols[i]}, cache:'no-cache'}).then(function(response) {
      return response.json();
    }).then(function(data) {
      allData[option_symbols[i]].push(data.optionChain.result[0]);
      console.log(allData[option_symbols[i]][0]);
                                            
      let myExpirations = [];
      for (let j = 0; j < allData[option_symbols[i]][0].expirationDates.length; j++) {
        if (within_two_weeks(allData[option_symbols[i]][0].expirationDates[j])) 
          myExpirations.push(allData[option_symbols[i]][0].expirationDates[j]);
      }
      console.log(myExpirations);
      expirations.push(myExpirations);      
    });
  }
  
  
                                                                 
                                                                 
</script>
