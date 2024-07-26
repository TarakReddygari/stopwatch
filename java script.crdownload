let timer;
let isRunning = false;
let lapCount = 1;

function toggleStartStop() {
  const startStopButton = document.getElementById('startStop');
  createStars(startStopButton);
  
  if (isRunning) {
    clearInterval(timer);
    startStopButton.innerText = 'Start';
  } else {
    timer = setInterval(updateDisplay, 1000);
    startStopButton.innerText = 'Stop';
  }
  isRunning = !isRunning;
}

function resetTracker() {
  createStars(document.getElementById('reset'));
  clearInterval(timer);
  document.getElementById('display').innerText = '00:00:00';
  document.getElementById('startStop').innerText = 'Start';
  document.getElementById('laps').innerHTML = '';
  isRunning = false;
  lapCount = 1;
}

function recordLap() {
  createStars(document.getElementById('recordLap'));
  const display = document.getElementById('display').innerText;
  const lapList = document.getElementById('laps');
  const lapItem = document.createElement('li');
  lapItem.innerText = `Lap ${lapCount}: ${display}`;
  lapList.appendChild(lapItem);
  lapCount++;
}

function updateDisplay() {
  const display = document.getElementById('display');
  const time = display.innerText.split(':');
  let seconds = parseInt(time[2], 10);
  let minutes = parseInt(time[1], 10);
  let hours = parseInt(time[0], 10);

  seconds++;

  if (seconds === 60) {
    seconds = 0;
    minutes++;
  }
  if (minutes === 60) {
    minutes = 0;
    hours++;
  }

  const formattedTime = `${padZero(hours)}:${padZero(minutes)}:${padZero(seconds)}`;
  display.innerText = formattedTime;
}

function padZero(value) {
  return value < 10 ? '0' + value : value;
}

function createStars(button) {
  const starContainer = document.createElement('div');
  starContainer.classList.add('button-star');
  
  for (let i = 0; i < 10; i++) {
    const star = document.createElement('div');
    star.classList.add('star');
    star.style.left = `${Math.random() * 100}%`;
    star.style.top = `${Math.random() * 100}%`;
    starContainer.appendChild(star);
  }
  
  button.appendChild(starContainer);
  
  setTimeout(() => {
    starContainer.remove();
  }, 600);
}
