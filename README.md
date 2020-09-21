<!DOCTYPE html>
<html>


    <head>
        <meta charset="utf-8">
        <title>MY PAGE</title>
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

        <style>

        body {
          background: url(https://cdn.pixabay.com/photo/2018/05/28/12/09/time-3435879_1280.jpg);
          font-family: Arial, sans-serif;
          font-size: 20px;
        }

        p{
          position: relative;
          right: 80px;
          font-size: 60px;
          font-weight: 900;
          text-align: right;
          color: #fff;
        }

        h1{
          position: relative;
          left: 40px;
          font-weight: bolder;
          font-size: 60px;
          font-weight: 900;
          margin-left;
          color: #fff;
        }

        button{
          padding: 14px 35px;
          border-radius: 3px;
          position: relative;
          left: 40px;
          font-size: 20px;
          background-color: #fff;
          color: 	#fec4c3;
          border-width: 0px;
          border-color: white;
          font-weight: 900;
        }

        label{
          font-weight: 900;
          position: relative;
          left: 50px;
          color: 	#fff;
        }


        	input{
            position: relative;
            left: 40px;
            border-style: none;
            font-size: 20px;
            font-weight: 900;
            color: 	#fec4c3;
            background-color: #fff;
        	}

        </style>


    </head>
    <body>

      <h1> COUNTDOWN </h1>

      <p id="timer" ></p>

      <input id="y" placeholder="YEAR" type="text" size="7"/><label>YEAR</label><br>
      <input id="mo" placeholder="1 to 12" type="text" size="7"/><label>MONTH</label><br>
      <input id="d" placeholder="1 to 31" type="text" size="7"/><label>DAY</label><br>
      <input id="h" placeholder="0 to 24" type="text" size="7"/><label>HOUR</label><br>
      <input id="mi" placeholder="0 to 59" type="text" size="7"/><label>MINUTES</label><br>
      <input id="s" placeholder="0 to 59" type="text" size="7"/><label>SECONDS</label><br><br>

      <button id="button">SET YOUR DATE</button>

      <script>

    // on button click check the inputs and then start the countdown
    $("#button").click(function(){

    // check inputs are correct
    if(
      isNaN($("#y").val()) || isNaN($("#mo").val()) || isNaN($("#d").val())
      || isNaN($("#h").val()) || isNaN($("#mi").val()) || isNaN($("#s").val())
      )
      {alert("Please, fill all fields only with numbers");}

      else if(   $("#y").val() < new Date().getFullYear())
      {alert("Please do not set year from the past");}
      else if(   $("#mo").val() > 12  || $("#mo").val() < 1  )
      {alert("Please, fill a month between 1 and 12");}
      else if(   $("#d").val() > 31  || $("#mo").val() < 0)
      {alert("Please, fill a day between 1 and 31");}
      else if(   $("#h").val() > 23  || $("#mo").val() < 0)
      {alert("Please, fill an hour between 0 and 23");}
      else if(   $("#mi").val() > 59  || $("#mo").val() < 0)
      {alert("Please, fill minutes between 0 and 59");}
      else if(   $("#s").val() > 59  || $("#mo").val() < 0)
      {alert("Please, fill seconds between 0 and 59");}

    else {

    // inputs are filled in dueDate
    var dueDate = new Date($("#y").val(), $("#mo").val()-1, $("#d").val(),
                            $("#h").val(), $("#mi").val(), $("#s").val(), 0);
    // inform if date set is already expired
    if(dueDate< new Date()){
    alert("Date set is already expired");
    }

    else{
    // function is executed every seconds
    x = setInterval(function() {
    // find time left to due date
    
    var timeLeft = dueDate - new Date();
    // calculate time left in each unit (days, months etc)
    var days = Math.floor( timeLeft/ (1000*60*60*24));
    var hours = Math.floor(timeLeft / (1000*60*60)) - days*24;
    var minutes = Math.floor(timeLeft / (1000*60)) - hours*60 - days*24*60;
    var seconds = Math.floor(timeLeft / (1000)) - minutes*60 - hours*60*60 - days*24*60*60;
    // display the countdown
    document.getElementById("timer").innerHTML = days + "d " + hours + "h "
    + minutes + "m " + seconds + "s ";
    // when countdown is over display text
    if (timeLeft < 0) {
    clearInterval(x);
    document.getElementById("timer").innerHTML = "YOUR BIG DAY IS FINALLY HERE!";
    }

    }, 1000);

  }
}
});

     </script>
    </body>
</html>
