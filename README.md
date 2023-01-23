# code
1.paint 
import React, { useState } from "react";
import "../styles/App.css";
import Selection from "./Selection";
import ColourSelector from "./ColourSelector";

const colourConfig = [
  {
    key: "blue",
    label: "Blue",
    classname: "btn-blue",
    background: "rgb(34, 193, 195)"
  },
  {
    key: "orange",
    label: "Orange",
    classname: "btn-orange",
    background: "rgb(221, 112, 18)"
  },
  {
    key: "green",
    label: "Green",
    classname: "btn-green",
    background: "rgb(44, 209, 88)"
  }
];

const title = "Select the gradient and then the Box to change the color";

const App = () => {
  let [nextBackground, selectNextBackground] = useState({ background: "" });
  const applyColor = (updateSelectionStyle) => {
    updateSelectionStyle(nextBackground);
  };

  return (
    <div id="master">
      <h5 className="heading">{title}</h5>

      <div className="row">
        {colourConfig.map((config, index) => (
          <ColourSelector
            key={config.key}
            config={config}
            selectNextBackground={selectNextBackground}
          />
        ))}
      </div>

      <div className="row" id="children-wrapper">
        {["selection1", "selection2", "selection3"].map((key) => (
          <Selection key={key} applyColor={applyColor} />
        ))}
      </div>
    </div>
  );
};

export default App;
import React from "react";

const ColourSelector = (props) => {
  const { config, selectNextBackground } = props;
  const { background } = config;
  return (
    <button
      className={config.classname}
      onClick={() => selectNextBackground({ background: background })}
    >
      {/* label should come here */}
      {config.label}
    </button>
  );
};
export default ColourSelector;

import React, { useState } from "react";
import "../styles/Child.css";

export default function Selection({ applyColor }) {
  let [color, setColor] = useState({ background: "" });
  return (
    <div className="fix-box" style={color} onClick={() => applyColor(setColor)}>
      <h2 className="subheading">Selection</h2>
    </div>
  );
}

2.debugging challenge keyword 

import React, { useEffect, useState } from "react";
import '../styles/App.css';

const App = () => {

  let [count, setCount] = useState(0)

  return (
    <div className="ball">
      <h1 className="count" onDoubleClick={() => { alert("cant edit it") }}>{count}</h1>
      <button className='increment-button' onClick={() => { setCount(count + 1) }}>Increment</button>
    </div>
  )
}


export default App;
h1 {
    color: #27aedb;
    text-align: center;
    }
    

button{
    color: #27aedb;
    text-align: center;
    justify-content: center;
    align-items: center;
}

3.Greetings with Props

import React from "react";
import '../styles/App.css';
import Welcome from './Welcome';

const App = () => {
  return (
    <Welcome name="Abhimanyu" />
  )
}


export default App;
// write code for Welcome component here
import React from 'react'


export default function Welcome(props) {
  return (
    <div>
      <h1>Hey {props.name}!</h1>
     <h2>Welcome to Newton School</h2>
    </div>
  )
}

4.Render React Component

import React, {Component, useState} from "react";
import '../styles/App.css';

const App = () => {
  return (
    <div id="main">
    <p>I am learning React. My life is getting better.</p>
    </div>
  )
}


export default App;

5.Rendering Multiple Components with React

import React, {Component, useState} from "react";
import '../styles/App.css';

const App = () => {
  return (
    <div id="main">
       <h1 data-ns-test="project-name" >Myntra Clone</h1>
       <h2 data-ns-test="project-description" >It is about the commerical website where we see some product of clothing and also add the product into bag</h2>
    </div>
   

    
  )
}


export default App;

6.React Dynamic Calc

import React,{useState,useEffect} from 'react'
import '../styles/App.css';

const App = () => {
  const [data, setData]= useState(0);
  const [data1, setData1]= useState(0);
  const [result, setResult]= useState(0);
  
  useEffect(() =>{
   setResult(data + data1);
  },[data, data1]);
  

 function handleChnage(e){
    let number = (Number(e.target.value));
    if(e.target.dataset.name === "one") {
      setData(number);
    } else {
      setData1(number);
    }
 };
 
  return (
    <div id="main">
      <input id='input1' data-name='one' onChange={handleChnage}/>
        +
      <input id='input2' data-name='two' onChange={handleChnage}/> 
      
      <p id='result'>{result}</p>
    </div>
  )
}


export default App;

7.Holiday Cities List

import React, { Component, useState } from "react";
import "../styles/App.css";

class App extends Component {
  constructor(props) {
    super(props);

    this.cityList = [
      { name: "Goa", country: "India" },
      { name: "Amsterdam", country: "Netherlands" },
      { name: "New York", country: "USA" },
      { name: "Darjeeling", country: "India" },
      { name: "Tokyo", country: "Japan" },
      { name: "Lonavala", country: "India" },
      { name: "Brandenburg Gate", country: "Germany" },
      { name: "Reichstag Building", country: "Germany" },
      { name: "Museum Island", country: "Germany" },
      { name: "Munnar", country: "India" },
      { name: "Leh Ladakh", country: "India" },
      // { name: "Goa", country: "India" },
      { name: "Agra", country: "India" },
      { name: "Dalhousie", country: "India" },
      { name: "Coorg", country: "India" },
      { name: "Rome", country: "Italy" },
      { name: "Milan", country: "Italy" },
      { name: "Venice", country: "Italy" },
      { name: "Varanasai", country: "India" },
      { name: "Jaipur", country: "India" },
      { name: "The Hofburg", country: "Austria" },
      { name: "Belvedere Palace", country: "Austria" },
      { name: "St. Stephen Cathedral", country: "Austria" },
      { name: "Kahna National Park", country: "India" },
      { name: "Amritsar", country: "India" },
      { name: "Mussoorie", country: "India" },
      { name: "Mount Abu", country: "India" },
      { name: "Tirupati", country: "India" }
    ];

    this.indianCity = this.cityList.filter(function (city) {
      return city.country === "India";
    });
  }
  // Goa(India), Amsterdam(Netherlands), New York(USA), Darjeeling(India), Tokyo(Japan), Lonavala(India)
  render() {
    let i = 1;
    return (
      <div id="main">
        <ol>
          {this.indianCity.map((item, index) => {
            if (
              item.name === "Goa" ||
              item.name === "Amsterdam" ||
              item.name === "New York" ||
              item.name === "Darjeeling" ||
              item.name === "Tokyo" ||
              item.name === "Lonavala"
            ) {
              let tempKey = "location" + i;
              i++;
              return (
                <li key={tempKey}>
                  {item.name},{tempKey}
                </li>
              );
            }
          })}
        </ol>
      </div>
    );
  }
}

export default App;

8.React stateful list - 1

import React, { useState } from "react";

const data = {
  "2018": ["Avengers 1", "Now you see me", "Fast and Furious 7"],
  "2019": ["Avengers 2", "Now you see me 2", "Fast and Furious 8"],
  "2020": [
    "Final Avengers Movie(Iron man dies)",
    "Now you finally used Lenskart",
    "Covid Came"
  ],
  "2021": ["Covid Returns"],
  "2022": ["Adventures of Saiman", "Adventures of Shaktiman"]
};
const App = () => {
  const [select, setSelect] = useState(null);

  return (
    <div id="main">
      <h1>hiii</h1>
      <select
        value={select}
        onChange={(e) => {
          setSelect(e.target.value);
        }}
      >
        {" "}
        <option selected value={null}></option>
        <option value="2018">2018</option>
        <option value="2019">2019</option>
        <option value="2020">2020</option>
        <option value="2021">2021</option>
        <option value="2022">2022</option>{" "}
      </select>
      <div id="selected-year">
        {select ? `Selected year-${select}` : "No year selected"}
        <ul>
          {select
            ? data[select].map((item) => {
                return <li>{item}</li>;
              })
            : ""}
        </ul>
      </div>
    </div>
  );
};

export default App;

9.Import Export React
import React, { Component, useState } from "react";
import '../styles/App.css';
import Heading from "./Heading";
import InputQuery from "./InputQuery";
import SubHeading from "./SubHeading";
import SubmitButton from "./SubmitButton";

const App = () => {
  return (
    <div id="main">
      <Heading />
      <InputQuery />
      <SubHeading />
      <SubmitButton />
    </div>
  )
}
export default App
import React from 'react'

function Heading() {
    return (
        <h1>Welcome to our Site.</h1>
    )
}
export default Heading

import React from 'react'

function InputQuery() {
    return (
        <input placeHolder={'Enter your query here..'} />
    )
}
export default InputQuery

import React from 'react'

function SubHeading() {
    return (
        <h5>Happy to solve you doubts.</h5>
    )
}
export default SubHeading

import React from 'react'

function SubmitButton() {
    return (
        <button>Ask</button>     
    )
}
export default SubmitButton

10.Youtube-liker---React-

import React from 'react'
import '../styles/App.css';
import like from '../like.svg';
const App = () => {
const [count,setCount] = React.useState(0)
const handleClick = () =>{
  setCount(count=>count+1)
}
  return (
    <div id="main">
      <img id="like-btn-img" src={like} style={{fill:'white',width:'100px',backgroundColor:`rgba(255,0,0,${0.1*count})`}} onClick={handleClick}/>
      <h3>Likes: <span id="like-counter">{count}</span></h3>
    </div>
  )
}


export default App;

11.Marco Polo

import React, { useState } from 'react'
// import '../styles/App.css';
const App = () => {
  const[data,setData]=useState("Marco")
  const[data1,setData1]=useState("Polo")

  function handleClick(){
    return(
    setData(data1),
    setData1(data)
    )
  }
  return (
    <div id="main">
    <h1 id="marco-polo">{data}</h1>
    <button id="marco-polo-toggler"onClick={handleClick}>{data1}</button>
    </div>
  )
}


export default App;

12.React-Array-As-Props

import React from 'react'
import '../styles/App.css';
const arr = JSON.parse(window.localStorage.getItem('props') || `["hello","world"]`) // do not change
const Join = (props) =>{
  return(
    <div id ="join">
      {/* Access prop 'words' and print it using .join like words.join(',')*/}
      {props.words.join(',')}

    </div>
  )
}
const App = () => {

  return (
    <div id="main">
      <Join words={arr} />
    </div>
  )
}


export default App;

13.tv remote

import React from 'react'
import '../styles/App.css';
const App = () => {

  let power=false;

function display(number)
{
  if(power===true){
    let present=document.getElementsByClassName('tv-container')[0].innerHTML;
    console.log(number);
    present+=`<center> <span style="margin-left:10px; display:inline-block;"></span> <center>`+number;
    document.getElementsByClassName('tv-container')[0].innerHTML=present;
    document.getElementById(number).classList.add('active-channel');
    setTimeout(function() { document.getElementById(number).classList.remove('active-channel') } , 500);
    

  }
 
  
}

function reset(){
  power=!power;

  if(power===false)
  {
    document.getElementsByClassName('tv-container')[0].innerHTML='<center>Power Off<center>';
    document.getElementById('container').style.backgroundColor='black';
  }
  else{
    document.getElementsByClassName('tv-container')[0].innerHTML='';
    document.getElementById('container').style.backgroundColor='dark-grey';
  }
  
}

function colorchange()
{
  document.getElementsByClassName('dot')[0].classList.add('clicked');
    document.getElementsByClassName('dot')[1].classList.add('clicked');
  
    setTimeout(function() { document.getElementsByClassName('dot clicked')[0].classList.remove('clicked') } , 500);
    setTimeout(function() { document.getElementsByClassName('dot clicked')[0].classList.remove('clicked') } , 500);
}
  return (
    
    <div id="main">
        <div className="wrapper">
        <div className="tv-space">
          <div className="tv-border">
            <div className="tv-container" id="container"style={{"color": "white",  "fontFamily": "roboto/serif",  "padding": "10px"}}>
              <center>Power Off</center>
            </div>
            <div className="tv-nav" style={{"textAlign":"center"}}>
              <br/> <span className="dot"></span> <br/><br/>
            </div>
          </div>
          
        </div>
        
        
        <div className="pult">
          <span className="dot"></span>
          <div className="block title"></div>
          <div className="block block-navigate">
            
            <button type="button" className="btn top-navigate power-off" id="power-off" onClick={reset} onMouseDown={colorchange}></button>
           
          </div>
          <div className="block block-channel">
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(1)} onMouseDown={colorchange} id="1">1</button>
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(2)} onMouseDown={colorchange} id="2">2</button>
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(3)} onMouseDown={colorchange} id="3">3</button>
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(4)} onMouseDown={colorchange} id="4">4</button>
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(5)} onMouseDown={colorchange} id="5">5</button>
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(6)} onMouseDown={colorchange} id="6">6</button>
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(7)} onMouseDown={colorchange} id="7">7</button>
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(8)} onMouseDown={colorchange} id="8">8</button>
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(9)} onMouseDown={colorchange} id="9">9</button>
            <button type="button" className="btn channel cnl-namber" onClick={()=> display(0)} onMouseDown={colorchange} id="0">0</button>
          
          </div>
          
         
         </div>
        </div>
    

    </div>
  )
}


export default App;
  
14.react text colour
  
  import React, {useEffect, useState} from 'react'
import '../styles/App.css';

const App = () => {
  const [changeColor, setChangeColor] = useState(false);

const handleClick=()=>{
  setChangeColor(!changeColor)
}

  return (
    <div id="main">
      <p className={`${(changeColor===true)?'blueColor':'redColor'}`} >Newton School</p>
      <button id='button' onClick={handleClick}>Change Style</button>
    </div>
  )
}


export default App;
  
  15.Outputting-Dynamic-data-in-
  
  import React,{useState,useEffect} from 'react'
import '../styles/App.css';
const App = () => {
  const [input,setInput]=useState("")
  const [input1,setInput1]=useState("-----")
//code here
function handlechange(e){
  return(
 setInput(e.target.value)
  )
}
function handleclick(e){
  return(
 setInput1(input)
  )
}
  return (
    <div id="main">
      <input id='input' onChange={handlechange}></input>
      <button id='button' onClick={handleclick}>Click</button>
      <p id='text'> Hello my name is {input1} and I study at Newton School</p>
    </div>
  )
}


export default App;
  
  16.Relatives List React
  
  import React, {Component, useState} from "react";
import '../styles/App.css';

class App extends Component {
    render() {

        return(
            <div id="main">
               <ol key="relativeList">
                <li key="relativeListItem1">Fufaji</li>
                <li key="relativeListItem2">Tauji</li>
               </ol>
            </div>
        )
    }
}


export default App;
  
  17.React Component on DOM Node
  
  import React from "react";

export default function App() {
    return (
      <div className="App">
      <p>Now I can render any React component on any DOM node I want using ReactDOM.render </p>
      </div>
    );
  }
  
  import React from "react";
import ReactDOM from "react-dom";
import App from "./components/App";

ReactDOM.render(<App />, document.getElementById("root"));

18.event handler 1
  
  import React from 'react'
import '../styles/App.css';
const App = () => {

  // do not change the code inside the function clickA
  const clickA = () =>{
    console.log('Clicked button A')
  }
  return (
    <div id="main">
      <button id="button-a" onClick={clickA}>Button A</button>
    </div>
  )
}
export default App;
  
  19.Event-Handler---2-
  
  import React from 'react'
import '../styles/App.css';
const App = () => {

  const handleClick = (event) =>{
    // use console.log
    // console.log("Button id is:-",event.target.id);
    console.log(`Button id is:-${event.target.id}`);

    'Button id is:-button-a'
  }

  // do not remove the two buttons or change their id
  return (
    <div id="main">
      <button id="button-a" onClick={handleClick}>Button A</button>
      <button id="button-b" onClick={handleClick}>Button B</button>
    </div>
  )
}


export default App;
  
  20.Event-Handler---3
  
  import React from 'react'
import '../styles/App.css';
const App = () => {

  const handleInput = (event) =>{
   console.log('Input in #'+ event.target.id+ ' is ' +event.target.value)
  }

  // do not change id of input elements
  return (
    <div id="main">
      <label htmlFor='text-input'>Text Input:- </label>
      <input onChange={handleInput} id="text-input" type={'text'} />

      <br/>
      <br/>

      <label htmlFor='num-input'>Number input</label>
      <input onChange={handleInput} id="num-input"  type={'number'} />
      <br/>
    </div>
  )
}


export default App;
  
  21.Toggle-Buttons-
  
  import React, {useState} from 'react'
import '../styles/App.css';
const App = () => {
//code here 
  const [on, setOn] = useState("ON")
  const [off, setOff] = useState("OFF")

  const handleClick= () => {
    setOn(off)
    setOff(on)    
  }

  
  return (
    <div className="App">
      <button id="btn1" onClick={handleClick}>
      {off}
      </button>
      <br />
      <br />
      <button id="btn2" onClick={handleClick}>
        {on}
      </button>
    </div>
  );
}


export default App;
  
 22. Event Handler - 4
  
  import React from 'react'
import '../styles/App.css';
const App = () => {

  const handleDoubleClick = (event) =>{
  
    switch (event.detail) {
      case 1: {
        console.log('I was not double clicked');
        break;
      }
      case 2: {
        console.log('I was double clicked');
        break;
      }
        default: {
        break;
      }
    }
  };
  
  return (
    <div id="main">
      <button id="dblclick-btn" onClick={handleDoubleClick} >Double click me</button>
    </div>
  )
}


export default App;
  
 23. event handler 5
  
  import React from "react";
import '../styles/App.css';
const App = () => {
  const handleSumbit = (event) => {
    event.preventDefault();
    console.log("form submitted");
  };
  return (
    <div id="main">
      <form onClick={handleSumbit}>
        <label htmlFor="name">Name</label>
        <input id="name" type="text" />

        <br />
        <br />
        <button type="submit">
          Submit
        </button>
      </form>
    </div>
  );
};

export default App;
  
  24.react drum machine
  
  app.js
  import React, { useState } from "react";
import "../styles/App.css";
import Pads from "./Pads";

export const bank1 = {
  Q: {
    name: "Heater 1",
    source: "https://s3.amazonaws.com/freecodecamp/drums/Heater-1.mp3"
  },
  W: {
    name: "Heater 2",
    source: "https://s3.amazonaws.com/freecodecamp/drums/Heater-2.mp3"
  },
  E: {
    name: "Heater 4",
    source: "https://s3.amazonaws.com/freecodecamp/drums/Heater-4_1.mp3"
  },
  A: {
    name: "Heater 3",
    source: "https://s3.amazonaws.com/freecodecamp/drums/Heater-3.mp3"
  },
  S: {
    name: "Clap",
    source: "https://s3.amazonaws.com/freecodecamp/drums/Heater-6.mp3"
  },
  D: {
    name: "Open Hi-Hat",
    source: "https://s3.amazonaws.com/freecodecamp/drums/Dsc_Oh.mp3"
  },
  Z: {
    name: "Kick n Hat",
    source: "https://s3.amazonaws.com/freecodecamp/drums/Kick_n_Hat.mp3"
  },
  X: {
    name: "Kick",
    source: "https://s3.amazonaws.com/freecodecamp/drums/RP4_KICK_1.mp3"
  },
  C: {
    name: "Closed Hi-Hat",
    source: "https://s3.amazonaws.com/freecodecamp/drums/Cev_H2.mp3"
  }
};

function ControlScreen({ volume, volumeHandler, on, onHandler }) {
  return (
    <div id="control-screen">
      <label id="label-power">
        <input type="checkbox" id="power" onClick={() => onHandler()} />
        <span className="checkmark">{on ? "ON" : "OFF"}</span>
      </label>
      <label id="label-volume">
        <input
          type="range"
          id="volume"
          value={volume}
          onChange={(e) => volumeHandler(e.target.value)}
        />
        <span id="volume-display">Volume : {volume} </span>
      </label>
    </div>
  );
}

function App() {
  const [volume, setVolume] = useState(0);
  const [on, setOn] = useState(false);

  const volumeHandler = (val) => {
    setVolume(val);
  };

  const onHandler = () => {
    setOn(!on);
  };

  return (
    <div id="drum-machine">
      <Pads power={on} />
      <br />
      <br />
      <br />
      <ControlScreen
        volume={volume}
        volumeHandler={volumeHandler}
        on={on}
        onHandler={onHandler}
      />
    </div>
  );
}

export default App;
  pad.js
  import React, { useRef } from "react";
import { bank1 } from "./App";

function Pad({ handleClick, power, backgroundStyle, element, id }) {
  const audio = new Audio(bank1[element].source);

  window.addEventListener("keydown", (event) => {
    if (event.key === element || event.key === element.toLowerCase()) {
      handleClick(bank1[element]);
      audio.play();
    }
  });

  return (
    <button
      data-tag={id}
      type="button"
      className="drum-pad"
      onClick={() => {
        audio.play();
        handleClick(bank1[element]);
      }}
      id={bank1[element]}
      disabled={!power}
      style={{ background: `${backgroundStyle}` }}
    >
      {element}
      <audio id={element} src={bank1[element].source} className="clip"></audio>
    </button>
  );
}

export default Pad;
  
  pads.js
  
  import React, { useEffect, useState } from "react";
import Pad from "./Pad";
import { bank1 } from "./App";

function Pads({ power }) {
  const keypadCode = Object.keys(bank1);
  const [audioName, setAudioName] = useState(null);

  const playSound = (e) => {
    setAudioName(e.name);
  };

  return (
    <div id="div-pads">
      {keypadCode.map((pad, idx) => {
        // console.log(pad + idx);
        return (
          <Pad
            id={pad + idx}
            key={pad + idx}
            handleClick={playSound}
            element={pad}
            power={power}
          />
        );
      })}
      <div id="display"> {audioName} </div>
    </div>
  );
}

export default Pads;
  
 25. Newspaper
  
  import React, {useState, useEffect} from 'react';
import '../styles/App.css';
import data from '../data.js';

const weatherAPI = {
  key: "a64d07a306972de8e9f8c8267a9cc2c0",
  base: "https://api.openweathermap.org/data/2.5/"
}

const newsAPI = {
  key: "1321740c80c3874a09a04e802b81c02a",
  base: "https://gnews.io/api/v4/"
}


function App() {
  const [query, setQuery] = useState('');
  const [weather, setWeather] = useState({main:{temp: ''},name: '', sys: {country: ''}, weather: [{main: ''}]});
  const [news, setNews] = useState(data);
  const search = evt => {
    if (evt.key === "Enter") {
      fetch(`${weatherAPI.base}weather?q=${query}&units=metric&APPID=${weatherAPI.key}`)
        .then(res => {
          if (res.ok) 
          return res.json();
          else{
            setQuery('');
            throw new Error('Invalid location/city/country');
          }
        })
        .then(result => {
          setWeather(result);
          setQuery('');
          console.log(result);
        })
        .catch((error) => {
          console.log(error)
        });
    }
  }
  const changeLan = async(L) => {
    if(L === 'English'){
      await fetch(`${newsAPI.base}top-headlines?&lang=en&token=${newsAPI.key}`)
            .then(res => {
              if(res.ok)
                return res.json();
              else
              throw new Error('Internel server error');
            }).then(function (data) {
              setNews(data);
            })
            .catch(error => console.log(error));
    } else {
        await fetch(`${newsAPI.base}top-headlines?&lang=hi&token=${newsAPI.key}`)
              .then(res => {
                if(res.ok)
                  return res.json();
                else
                throw new Error('Internel server error');
              }).then(function (data) {
                setNews(data);
              })
              .catch(error => console.log(error));
    }
  }
  useEffect(() =>{
    const fetchWeather = async () =>{
      if(navigator.geolocation){
        navigator.geolocation.getCurrentPosition(async (position) =>{
          // get user's location
          let pos = {
            lat: position.coords.latitude,
            lon: position.coords.longitude, 
          }
          // get whether of user's location
          await fetch(`${weatherAPI.base}weather?lat=${pos.lat}&lon=${pos.lon}&units=metric&appid=${weatherAPI.key}`)
          .then(res => {
            if (res.ok)
              return res.json();
            else
              throw new Error('Invalid location/city/country');
          })
          .then(result => {
            setWeather(result);
            console.log(result);
          })
          .catch(error => console.log(error));
        });
      }
    }
    const fetchNews = async () =>{
      if(news.articles.length === 1){
        await fetch(`${newsAPI.base}top-headlines?&lang=hi&token=${newsAPI.key}`)
          .then(function (response) {
              if(response.ok)
              return response.json();
            else
              throw new Error('Something went wrong')
          })
          .then(function (data) {
            setNews(data);
            console.log(data);
          })
          .catch(error => console.log(error));
        }
    }
   fetchWeather();
   fetchNews();
  }, [])
  

  const dateBuilder = (d) => {
    let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
    let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

    let day = days[d.getDay()];
    let date = d.getDate();
    let month = months[d.getMonth()];
    let year = d.getFullYear();

    return `${day} ${date} ${month} ${year}`
  }
  
  return (
    <div className="App">
    <div className='weather-info'>
    <div className="weather-search-box">
      <input className="search" type="text" onChange={e => setQuery(e.target.value)} placeholder="search.." value={query} onKeyPress={search}></input>
    </div>
    <div className="location-box">
            <div className="location">{weather.name}, {weather.sys.country}</div>
            <div className="date">{dateBuilder(new Date())}</div>
          </div>
      <div className="weather-box">
        <div className="temp">{Math.round(weather.main.temp)}°c</div>
        <div className="weather">{weather.weather[0].main}</div>
      </div>
      </div>
    <div className='lan'>
        <button onClick={() => changeLan('Hindi')} data-testid='lang-hi'>हिन्दी</button>
        <button onClick={() => changeLan('English')} data-testid='lang-en'>English</button>
      </div>
      <div className='news-info'>
          {news.articles.map((article) => {
            return <article className='article' key={article.title}>
            <a href={article.url}><h3>{article.title}</h3></a>
              <p>{article.description}</p>
              <img src={article.image} width='200px' height='200px'/>
            </article>
          })}
      </div>
    </div>
  );
}

export default App;

26.Adding List Names

import React, { useState, useEffect } from 'react'
import '../styles/App.css';
import List from "./List";
const App = () => {
  const [val, setValue] = useState("");
  const [list, setList] = useState([]);
  const changehandler = (event) => {
    setValue(event.target.value);
  }
  const addhandler = () => {
    setList([...list, val]);
  }
  return (
    <div id="main">
      <input id="input" value={val} onChange={changehandler} />
      <button id="button" onClick={addhandler}>Click</button>
      <ul id="list">

        {list.map((element, index) => {
          return <li className="items" key={element + index} >{element}</li>;
        })}

        {/* <List listx={list} /> */}
      </ul>
    </div>
  )
}


export default App;

27.Dynamic Context (1) Settings

upadte setting.js
import React from "react";
import { useContext } from "react";
import { UserContext } from "../context/userContext";

export const Settings = () => {
  // to be implemented in context
  const { changeGreeting } = useContext(UserContext);

  return (
    <div style={{ border: "5px solid red", padding: "8px" }} id="settings">
      <h4>Settings</h4>
      <input
        type={"text"}
        onChange={(event) => {
          changeGreeting(event.target.value);
        }}
      />
    </div>
  );
};

context .js
import React, { createContext, useState } from "react";

const UserContext = createContext();

const Wrapper = (props) => {
  const [greeting, setGreeting] = useState("Hello");
  const changeGreeting = (val) => {
    setGreeting(val);
  };

  return (
    <UserContext.Provider value={{ greeting, changeGreeting }}>
      {props.children}
    </UserContext.Provider>
  );
};
export { Wrapper, UserContext };

28.Context-Theme-Toggler-

LocalThemedBox.js
import React, { useContext, useEffect, useState } from 'react';
import { ThemeContext } from './ThemeProvider';

const LocalThemedBox = () => {

     const {theme} = useContext(ThemeContext);
    // console.log(theme);

    const [localTheme,setLocalTheme] = useState(theme);

    useEffect(() => {
        
        setLocalTheme(theme);
       let ini = theme === 'dark'? 'Toggle local theme to light' : 'Toggle local theme to dark';
       setLocalBtn(ini);

    },[theme])

const initial = localTheme === 'dark'? 'Toggle local theme to light' : 'Toggle local theme to dark';

     const [localBtn,setLocalBtn] = useState(initial)

    let localThemefn = () => {
        if(localBtn === 'Toggle local theme to dark'){
            // theme = 'dark';
           setLocalTheme('dark');
            setLocalBtn('Toggle local theme to light');
        }else{
            // theme = 'light';
            setLocalTheme('light');
            setLocalBtn('Toggle local theme to dark');
        }
    }
return(
    <div style={{width:'200px',height:'200px',border:'2px solid green'}} id="local-themed-box" className={'bg-'+localTheme}>
        {/* Write code below this line */}
        <p id="local-themed-text-container" className={'txt-'+localTheme}>hello</p>
        <button id="local-theme-toggler" onClick={localThemefn} className={`btn btn-${localTheme} txt-${localTheme}`}>{localBtn}</button>
    </div>
)
}

export { LocalThemedBox }

ThemeProvider.js 
import React, { useState } from 'react';

const ThemeContext = React.createContext()
const ThemeProvider = (props) =>{
     const [theme, setTheme] = useState('light')
    return (
        <React.Fragment>
            <ThemeContext.Provider value={{theme, setTheme}}>
                {props.children}
            </ThemeContext.Provider>
        </React.Fragment>
    )
}
export {ThemeProvider,ThemeContext}

ThemeToggleButton.js
import React, { useContext, useState } from 'react';
import { ThemeContext } from './ThemeProvider';

const ThemeToggleButton = () =>{
    
    const [toggle,setToggle] = useState('Switch to dark theme');
    //const [theme1,setTheme1] = useState('light');

    const {theme,setTheme} = useContext(ThemeContext);
    // console.log(theme);

    let global = () =>{

        if(toggle === 'Switch to dark theme'){
            setTheme('dark')
            setToggle('Switch to light theme');
        }else{
            setTheme('light');
            setToggle('Switch to dark theme');
        }
    }
    return (
       <>
       <button className={`btn btn-${theme} txt-${theme}`} id='global-theme-toggler' onClick={global}>{toggle}</button>
       </>
    )

}
export {ThemeToggleButton}

29.Conditional Logging in Counter

import React from 'react'
import '../styles/App.css';

class App extends React.Component{
  
  handleClick(){
    this.setState({count: this.state.count + 1})
  }
  constructor(props){
    super(props)
    this.state = {count:0}
    this.handleClick = this.handleClick.bind(this)
  }
  
  shouldComponentUpdate(nextProps,nextState){
  return nextState.count%2==0
  }


  render(){
    console.log(`Rendering with count:-${this.state.count}`)
    return(
      <div>
        <span id="count">{this.state.count}</span>
        <button id="incr-btn" onClick={this.handleClick}>Increment</button>
      </div>
    )

  }
}

export default App;

30.Odd-Even-Components-

import React from 'react'
import '../styles/App.css';

class Odd extends React.Component {
  componentWillUnmount(){
    console.log("Odd is unmounted")
  }
  // compo(){
  //   console.log("Odd is unmounted");
  // }

  render() {
    // console.log("Odd is unmounted");
    return (
      <div id="odd">
        I am odd
      </div>
    )
    
  }
}

class Even extends React.Component {
  componentWillUnmount(){
    console.log("Even is unmounted")
  }

  render() { 
    return (
      <div id="even">
        I am even
      </div>
    )
  }
}
class App extends React.Component {
  handleChange(){
    this.setState({even: !this.state.even})
  }
  constructor(props){
    super(props)
    this.state = {even: true}
    this.handleChange =  this.handleChange.bind(this)
  }
  render() {
    return (
      <div id="main">
        {this.state.even ? <Even /> : <Odd />}

        <button id="toggle" onClick={this.handleChange}>Change</button>
      </div>
    )
  }

}


export default App;

31.First Class Based Component

import React from 'react'
import '../styles/App.css';

class App extends React.Component {
    
    constructor(){
        super();
        this.state = {
            name: "John Doe",
            enrollmentNo: "12345678",
            age: 34
        }
    }

    

    render() {

        const handler = () => {
            let changeState = this.state.age;
            this.setState({age :changeState + 1 })
        }

        return (
            <>
            <h1>Hello, my name is {this.state.name}</h1>
            <p>I am {this.state.age} years old and my enrollment no is {this.state.enrollmentNo}</p>
            <button onClick={handler}>increament age</button>
            </>
        )
    }
}


export default App;


32.Class-based-Component

import React from 'react'
import '../styles/App.css';



class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  componentDidMount() {
    this.timerID = setInterval(
// write your code here
      () => {
        this.tick()
      },1000
 
    );
  }

  tick() {
    this.setState({
      date: new Date()
    });
    
  }

  render() {
    return (
      <div id='main'>
        <h1>Welcome to Newton School</h1>
        <div id='timer'>{this.state.date.toLocaleTimeString()}</div>
      </div>
    );
  }
}



export default App;

React-Router-easy-
