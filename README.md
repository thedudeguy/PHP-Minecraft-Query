PHP-Minecraft-Query
===================

A simple PHP class to connect to a minecraft server and get data about the server using the Query Protocol.

To connect to a server, Query must be activated on the minecraft server by setting `enable-query=true` in the server's server.properties.

This script connects to the server over UDP.

## Examples

### As a Regular PHP Library:
```php
require_once('query.php');

$server = new Query('some.minecraftserver.com');
//or new Query('some.minecraftserver.com', $port, $timeout);

if ($server->connect())
{
  $info = $server->get_info();
  print_r($info);
}

```

### As a CodeIgniter Library:
```php
$settings = array(
  'host' => 'some.minecraftserver.com', //required
  'port' => 25565,  //optional
  'timeout' = 3,    //optional
);
$this->load->library('query', $settings);

$this->query->connect();

if ($this->query->is_connected()) {
  $info = $this->query->get_info();
  print_r($info);
}
```

### get_info() result
Result is an array: here is the dump:
```
Array
(
    [hostname] => Server MOTD
    [gametype] => SMP
    [game_id] => MINECRAFT
    [version] => 1.7.2
    [plugins] => 
    [map] => world
    [numplayers] => 2
    [maxplayers] => 20
    [hostport] => 25565
    [hostip] => 127.0.1.1
    [players] => Array
    (
      [0] => player1
      [1] => player2
    )

)
```
