# NASA-API
Breakdown of my NASA Fact of the day Api project


I unfortunately lost the files since my old laptop crashed, but I will talk about the creation process 

link: https://apiproject1obada.netlify.app/
(thankfully I had it hosted)

This is my very first project where I used an API to retrieve data from a database coming from another computer.
I chose to make a fact of the day app. Everyday at the NASA DB, they have an object filled with info(a photo, video, description, date, and so much more)  
I used an HTML form( type="date") to pick a certain day, then I could use that input to search for the fact of the day uploaded on that date in the NASA DB. With Javacript. 

I used an standard API getfetch teamplate from Mozilla 

JS code looks something like this: 

document.querySelector('button').addEventListener('click', getFetch)

function getFetch(){
    const choice = document.querySelector("input").value
    const url = `https://api.nasa.gov/planetary/apod?api_key=jaI8lrnQIZUjURKsMtfSgEZN0gXfI5bbDrt3Olqr&date=${choice}`

  fetch(url)
      .then(res => res.json()) // parse response as JSON
      .then(data => {
        console.log(data)
        document.querySelector("h3").innerText = data.explanation
        
        if (data.media_type === "image"){
        document.getElementById("one").style.display = "block";
        document.querySelector("img").src = data.hdurl;
        document.getElementById("two").style.display = "none";
        } else if (data.media_type === "video"){
        document.getElementById("two").style.display = "block";
        document.querySelector("iframe").src = data.url;
        document.getElementById("one").style.display = "none";
    }
    })
      .catch(err => {
          console.log(`error ${err}`)
      });
}


Essentially by clicking the button (from HTML), it triggers the function of getFetch (function above), 
within the getFetch function the first thing I did was create a variable called choice, choice is the inputted date. 
That date gets added at the end of the link using backticks( `${}`) this way I can put the variable of choice within the url 
that fetches the object uploaded on that specific date. 
then the rest of the paragraph is how I parse through the data and handle things,(in case I get a video, or photo. I used a conditional very simple stuff.

The front end was designed using HTML and CSS, I tried my best to make it properly themed. 
