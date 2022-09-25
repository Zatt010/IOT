var net = require('net');
var textChunk = '';
var server = net.createServer(function(socket) {
	socket.write('callback server\r\n');
	socket.on('data', function(data){
		console.log(data);
		textChunk = data.toString('utf8');
		console.log('from server'+textChunk);
		socket.write(textChunk);
	});
});
server.listen(8080, '0.0.0.0');
console.log("Server iniciado");
