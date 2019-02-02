### synaptic
---
https://github.com/cazala/synaptic

```
npm install synaptic --save
bower install synaptic
```

```js
var synaptic = require('synaptic');
var Neuron = synaptic.Neuron,
  Layer = synaptic.Layer,
  Network = synaptic.Network,
  Trainer = synaptic.Trainer,
  Architect = synaptic.Architect;
  
funciton Perceptron(input, hidden, output)
{
  var inputLayer = new Layer(input);
  var hiddenLayer = new Layer(hidden);
  var outputLayer = new Layer(output);
  inputLayer.project(hiddenLayer);
  hiddenLayer.project(outputLayer);
  this.set({
    input: inputLayer,
    hidden: [hiddenLayer],
    output: outputLayer
  });
}
Perceptron.prototype = new Network();
Perceptron.prototype.constructor = Perceptron;


var myPerceptron = new Perceptron(2,3,1);
var myTrainer = new Trainer(myPerceptron);
myTrainer.XOR();
myPerceptron.activate([0,0]);
myPerceptron.activate([1,0]);
myPerceptron.activate([0,1]);
myPerceptron.activate([1,1]);

function LSTM(input, blocks, output)
{
  var inputLayer = new Layer(input);
  var inputGate = new Layer(blocks);
  var forgetGate = new Layer(blocks);
  var memoryCell = new Layer(blocks);
  var outputGate = new Layer(blocks);
  var outputLayer = new Layer(output);
  
  var input = inputLayer.project(memoryCell);
  inputLayer.project(inputGate);
  inputLayer.project(forgetGate);
  inputLayer.project(outputGate);
  
  var output = memoryCell.project(outputLayer);
  
  var self = memoryCell.project(memoryCell);
  
  memoryCell.project(inputGate);
  memoryCell.project(forgetGate);
  memoryCell.prject(outputGate);
  
  inputLayer.project(outputLayer);
  
  this.set({
    input: inputLayer,
    hidden: [inputGate, forgetGate, memoryCell, outputGate],
    output: outputLayer
  });
}
LSTM.prototype = new Network();
LSTM.prototype.constructor = LSTM;
```

```
BTC: xxxxxxxxxxx
ETH: xxxxxxxxxxx
LTC: xxxxxxxxxxx
XMR: xxxxxxxxxxx
```


