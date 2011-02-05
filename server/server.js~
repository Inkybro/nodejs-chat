//This file, server.js, is intended to be parsed by Node.JS
//It will act as the server for our chat application

var sys = require('sys');
var http = require('http');
var url = require('url');
var io = require('./socket.io');

var server;
var socket;
var clients;

var log = sys.puts;
var port = 4134;

function init() {
	
	//we need to setup the http server and accept any new client requests
	server = http.createServer();
	//tell the socket to listen closely
	socket = io.listen(server);
	
	//catch a new client connection
	socket.on('connection', function(client) {

		//handle a new client connection	
		onClientConnected(client);
		
		//now let's setup two event handlers for data and disconnections
		client.on('message', function(packet) { onClientSentData(client, packet); });
		client.on('disconnect', function(client) { onClientDisconnected(client); });
		
	});
	
	//setup a clients array to hold a list of connected clients
	clients = new Array();
	
	//let's bind to our specified port number at this point, and begin listening for any new connections
	server.listen(port);
	log('Server is now listening for new connections on port ' + port);
}



function onClientConnected(client) {
	//
}

function onClientSentData(client, packet) {
	log('A client has sent data packet "' + packet + '"');
	client.broadcast(packet);
}

function onClientDisconnected(client) {
	//
}

init();