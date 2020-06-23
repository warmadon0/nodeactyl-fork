Nodeactyl-Fork
=========

## Installation

``` npm i --save nodeactyl-fork ```

## Usage

```CLIENT

getAllServers()
Gets all servers a API key has access to

applicationAction.getAllServers().then((response) => {
   // response will be a JSON Array like below
}).catch((error) => {
    console.log(error);
});
```
Will Return Like This :
[
      {
         "object":"server",
         "attributes":{
            "server_owner":true,
            "identifier":"d3aac109",
            "uuid":"d3aac109-e5a0-4331-b03e-3454f7e136dc",
            "name":"Survival",
            "description":"",
            "limits":{
               "memory":1024,
               "swap":0,
               "disk":5000,
               "io":500,
               "cpu":200
            },
            "feature_limits":{
               "databases":5,
               "allocations":5
            }
         }
      },
      {
         "object":"server",
         "attributes":{
            "server_owner":true,
            "identifier":"d3aasd879",
            "uuid":"d3aac109-e5a0-4331-b03e-shdk87h7d783d",
            "name":"Creative",
            "description":"",
            "limits":{
               "memory":2048,
               "swap":512,
               "disk":10000,
               "io":500,
               "cpu":400
            },
            "feature_limits":{
               "databases":1,
               "allocations":2
            }
         }
      }
   ]

```CLIENT

killServer()
Kills a server

applicationAction.killServer("ServerID").then((response) => {
   // response will be "Server killed successfully"
}).catch((error) => {
    console.log(error);
});
```

```CLIENT

stopServer()
Stops a server

applicationAction.stopServer("ServerID").then((response) => {
   // response will be "Server stopped successfully"
}).catch((error) => {
    console.log(error);
});
```

```CLIENT

startServer()
Starts a server

applicationAction.startServer("ServerID").then((response) => {
   // response will be "Server started successfully"
}).catch((error) => {
    console.log(error);
});
```

```CLIENT

restartServer()
Restarts a server

applicationAction.restartServer("ServerID").then((response) => {
    // repsonse wil be "Server restarted successfully"
}).catch((error) => {
    console.log(error);
});
```

```CLIENT

sendCommand()
Sends a command to a currently online server.

applicationAction.sendCommand("ServerID", "CommandToSend").then((response) => {
    // Response will be "Command send successfully
}).catch((error) => {
    // Read the notice down below
    console.log(error);
});
```

```CLIENT

getServerStatus()
Gets the status of a running server

applicationAction.getServerStatus("ServerID").then((status) => {
    /** See the JSON object below
     * to see what response returns.
     */ 
}).catch((error) => {
    console.log(error);
});
```

{
	state: "on",
	memory: Object {
				current: 982,
				limit: 12288
			},
	cpu: Object {
			current: 8.714,
			cores: [3.425, 1.068, 1.74, 0.363, 1.239, 0.879],
			limit: 100},
	disk: Object {
			current: 2263,
			limit: 35840
			}
}

```CLIENT

getServerInfo()
Will get all the information about a server.

applicationAction.getServerInfo('ServerID').then(response => {
    /** See the JSON object below
     * to see what response returns.
     */ 
}).catch((error) => {
    throw error;
});
```

{
  server_owner: true,
  identifier: '47086b41',
  uuid: '47086b41-389a-4909-a114-dbf6f56e2d8b',
  name: 'Lobby',
  description: '...',
  limits: { memory: 12288, swap: 10, disk: 35840, io: 500, cpu: 100 },
  feature_limits: { databases: 2, allocations: 0 }
}

```CLIENT

isOwner()
Check if the API key holder is the owner of a server.

applicationAction.isOwner('af8c9137').then(response => {
    //do something with the infomation
    
    if (response === true) {
        //server is owned by API Key Holder
        console.log('API Key Holder is the owner of this server.')
    } 
    
    else {
        //server is not owned by API Key Holder
        console.log('API Key Holder is NOT the owner of this server.')
    }
});
```

```CLIENT

getCPUCores()
Get the CPU Information.

applicationAction.getCPUCores('ServerID').then(response => {
    /** See the JSON object below
     * to see what response returns.
     */ 
}).catch((error) => {
    throw error;
});
```

[
    0.033,
    0.048,
    0.04,    
    0,
    0.031,
    0,
    0.021,
    0.024,
    0.249,
    0.042,
    0.007,
    0,
    0.293,
    0.003,
    0.6,
    0.131
]

```CLIENT

getCPUUsage
Get CPU Usage

applicationAction.getCPUUsage('ServerID').then(response => {
    /** See the JSON object below
     * to see what response returns.
     */ 
}).catch((error) => {
    throw error;
});
```

{
    'current': 1.52,
    'limit': 200
}

```CLIENT

getRAMUsage()
Get the RAM Information.

applicationAction.getRAMUsage('ServerID').then(response => {
    /** See the JSON object below
     * to see what response returns.
     */ 
}).catch((error) => {
    throw error;
});
```

{
    "current": 234,
    "limit": 1024
}

```CLIENT

getDiskUsage()
Get the disk information.

applicationAction.getDiskUsage('ServerID').then(response => {
    /** See the JSON object below
     * to see what response returns.
     */ 
}).catch((error) => {
    throw error;
});
```

{
    "current": 657
    "limit": 10000
}

```ADMIN

updateUser()
Update a user using the application api

application.updateUser('UserID', 'username', 'password', 'email@example.com', 'first_name', 'last_name', true, 'en').then(user => {
    // Retuns object of the updated user
}).catch(err => {
    console.log(err);
})
```

```ADMIN

getUserInfo()
Grabs all a user's information available to a API key

application.getUserInfo("userID").then(user => {
    // Retuns object of the user (see below)
}).catch(err => {
    console.log(err);
})
```

{
  id: 1,
  external_id: null,
  uuid: '7c00ddc5-3785-45f9-a7cb-fe3ae0ecaf08',
  username: 'username',
  email: 'email@example.com',
  first_name: 'firstname',
  last_name: 'lastname',
  language: 'en',
  root_admin: true,
  '2fa': false,
  created_at: '2020-01-24T21:31:35+00:00',
  updated_at: '2020-01-24T21:31:35+00:00'
}

```ADMIN

getNodeInfo()
Grabs all a node's information available to a API key

application.getNodeInfo("NodeID").then(node => {
    // Retuns object of the node (see below)
}).catch(err => {
    console.log(err);
})
```

{
  object: 'node',
  attributes: {
    id: 1,
    public: true,
    name: 'NODE 1',
    description: 'NODE 1',
    location_id: 1,
    fqdn: '123.123.123.123',
    scheme: 'http',
    behind_proxy: false,
    maintenance_mode: false,
    memory: 3000,
    memory_overallocate: 0,
    disk: 10000,
    disk_overallocate: 0,
    upload_size: 100,
    daemon_listen: 8080,
    daemon_sftp: 2022,
    daemon_base: '/srv/daemon-data',
    created_at: '2020-01-24T21:33:38+00:00',
    updated_at: '2020-01-24T21:33:38+00:00'
  }
}

```ADMIN

getAllNodes()
Grabs all the nodes available to a API key

application.getAllNodes().then(nodes => {
    // Retuns an array of nodes (see below)
}).catch(err => {
    console.log(err);
})
```

[
  {
    object: 'node',
    attributes: {
      id: 1,
      public: true,
      name: 'NA-1',
      description: 'North America',
      location_id: 1,
      fqdn: '123.123.123.123',
      scheme: 'http',
      behind_proxy: false,
      maintenance_mode: false,
      memory: 62000,
      memory_overallocate: 0,
      disk: 500000,
      disk_overallocate: 30,
      upload_size: 100,
      daemon_listen: 8080,
      daemon_sftp: 2022,
      daemon_base: '/srv/daemon-data',
      created_at: '2019-12-13T08:53:40+00:00',
      updated_at: '2019-12-26T21:49:07+00:00'
    }
  },
  {
    object: 'node',
    attributes: {
      id: 2,
      public: true,
      name: 'Nodee',
      description: '',
      location_id: 1,
      fqdn: '0.0.0.0',
      scheme: 'http',
      behind_proxy: false,
      maintenance_mode: false,
      memory: 2000,
      memory_overallocate: 5,
      disk: 5000,
      disk_overallocate: 5,
      upload_size: 100,
      daemon_listen: 8080,
      daemon_sftp: 2022,
      daemon_base: '/srv/daemon',
      created_at: '2019-12-19T23:29:02+00:00',
      updated_at: '2019-12-19T23:29:02+00:00'
    }
  }
]

```ADMIN

getAllServers()
Gets all the server available to the API key.

application.getAllServers().then(servers => {
    // Retuns an array of servers (see below)
}).catch(err => {
    console.log(err);
})
```

[
  {
    object: 'server',
    attributes: {
      id: 24,
      external_id: null,
      uuid: 'd6df07f3-9448-4f5f-9310-b434fc3df90f',
      identifier: 'd6df07f3',
      name: "Our Private Server",
      description: 'Remember to not delete this dalton',
      suspended: false,
      limits: [Object],
      feature_limits: [Object],
      user: 1,
      node: 1,
      allocation: 22,
      nest: 1,
      egg: 3,
      pack: null,
      container: [Object],
      updated_at: '2019-12-27T23:20:59+00:00',
      created_at: '2019-12-23T03:06:19+00:00'
    }
  },
  {
    object: 'server',
    attributes: {
      id: 25,
      external_id: null,
      uuid: '96352174-1385-4bfd-bba3-e63ec9fc3c8d',
      identifier: '96352174',
      name: 'Spigot Testing',
      description: 'Server specifically designed for testing plugins',
      suspended: false,
      limits: [Object],
      feature_limits: [Object],
      user: 1,
      node: 1,
      allocation: 23,
      nest: 1,
      egg: 3,
      pack: null,
      container: [Object],
      updated_at: '2019-12-27T23:22:25+00:00',
      created_at: '2019-12-27T23:22:09+00:00'
    }
  }
]

```ADMIN

getAllUsers()
Gets all users attached to the panel

application.getAllUsers().then(users => {
    // Retuns an array of users (see below)
}).catch(err => {
    console.log(err);
})
```

[
  {
    object: 'user',
    attributes: {
      id: 1,
      external_id: null,
      uuid: 'bf347424-1c93-428d-8c10-5b3b3f5d076b',
      username: 'admin',
      email: 'email@email.com',
      first_name: 'user',
      last_name: 'name',
      language: 'en',
      root_admin: true,
      '2fa': false,
      created_at: '2019-12-13T08:38:23+00:00',
      updated_at: '2019-12-13T08:38:23+00:00'
    }
  },
  {
    object: 'user',
    attributes: {
      id: 2,
      external_id: null,
      uuid: 'ff9c337b-9d66-41da-b67e-729a8c9da97c',
      username: 'minestar',
      email: 'minestar@minestar.star',
      first_name: 'mine',
      last_name: 'star',
      language: 'en',
      root_admin: true,
      '2fa': false,
      created_at: '2019-12-13T09:02:55+00:00',
      updated_at: '2019-12-13T10:38:47+00:00'
    }
  }
]

```ADMIN

deleteServer()
Deletes a server with an InternalID

application.deleteServer("InternalID").then(server => {
    // Returns "Server deleted successfully"
}).catch(err => {
    console.log(err);
})
```

```ADMIN

deleteUser()
Deletes a user

application.deleteUser("UserID").then(user => {
    // Returns "User deleted successfully"
}).catch(err => {
    console.log(err);
})
```

```ADMIN

deleteNode()
Deletes a node

application.deleteNode("NodeID").then(node => {
    // Returns "Node deleted successfully"
}).catch(err => {
    console.log(err);
})
```

```ADMIN

createNode()
Creates a node

application.createNode("NodeName", "New Node Desc", "1", true, "FQND.com", "http", false, "5000", "10", "5000", "10", "/srv/daemon", "8080", "2022", false, "200").then(node => {
    // Returns a node object (see below)
}).catch(err => {
    console.log(err);
})
```

{
  id: 3,
  public: true,
  name: 'NodeName',
  description: '',
  location_id: 1,
  fqdn: 'FQND.com',
  scheme: 'http',
  behind_proxy: false,
  maintenance_mode: false,
  memory: 5000,
  memory_overallocate: 10,
  disk: 5000,
  disk_overallocate: 10,
  upload_size: 200,
  daemon_listen: 8080,
  daemon_sftp: 2022,
  daemon_base: '/srv/daemon',
  created_at: '2020-01-03T05:32:19+00:00',
  updated_at: '2020-01-03T05:32:19+00:00'
}

```ADMIN

createUser()
Creates a user

application.createUser("Username", "Password", "Email", "FirstName", "LastName", false, "en").then(user => {
    // Returns a user object (see below)
}).catch(err => {
    console.log(err);
})
```

{
  id: 9,
  external_id: null,
  uuid: 'ae0986de-2db1-4394-aad8-ee8e58b49734',
  username: 'username',
  email: 'Email@SomeEmail.net',
  first_name: 'FirstName',
  last_name: 'LastName',
  language: 'en',
  root_admin: false,
  '2fa': false,
  created_at: '2020-01-03T05:15:38+00:00',
  updated_at: '2020-01-03T05:15:38+00:00'
}

```ADMIN

createServer()
Creates a server using Nodeactyl

application.createServer("latest", "NameOfServer", "OwnerID", "PackID", "EggID", "DockerImage", "StartupCMD", "RAM", "Swap", "DiskSpace", "IO", "CpuCores", "MaxDatabases", "AmtOfAllocations").then(res => {
    // returns a server object (see below)
}).catch(error =>{
    console.log(error);
})
```

{
  id: 22,
  external_id: null,
  uuid: 'f049bcbd-58b1-4e11-aeca-863aae9c03bb',
  identifier: 'f049bcbd',
  name: 'NamOfServer',
  description: 'A Nodeactyl server',
  suspended: false,
  limits: { memory: 1024, swap: 0, disk: 10000, io: 500, cpu: 200 },
  feature_limits: { databases: 1, allocations: 1 },
  user: 1,
  node: 1,
  allocation: 27,
  nest: 1,
  egg: 1,
  pack: null,
  container: {
    startup_command: 'java -Xms128M -Xmx{{SERVER_MEMORY}}M -jar {{SERVER_JARFILE}}',
    image: 'quay.io/pterodactyl/core:java',
    installed: false,
    environment: {
      BUNGEE_VERSION: 'latest',
      SERVER_JARFILE: 'server.jar',
      STARTUP: 'java -Xms128M -Xmx{{SERVER_MEMORY}}M -jar {{SERVER_JARFILE}}',
      P_SERVER_LOCATION: 'US',
      P_SERVER_UUID: 'f049bcbd-58b1-4e11-aeca-863aae9c03bb'
    }
  },
  updated_at: '2019-12-22T07:35:17+00:00',
  created_at: '2019-12-22T07:35:17+00:00'
}

```ADMIN

suspendServer()
Suspend servers with the application api

application.suspendServer("InternalID").then(server => {
    // Retuns response from server
}).catch(err => {
    console.log(err);
})
```

```ADMIN

unSuspendServer()
Unsuspends servers with the application api.

application.unSuspendServer("InternalID").then(server => {
    // Retuns response from server
}).catch(err => {
    console.log(err);
})
```

## Setup

	```
			const node = require('nodeactyl-fork');
			//Test Client Part
			const application = node.Application;
			const applicationAction = node.Client;
			
			applicationAction.login('https://yourpanelhostname/', APIKEYCLIENT , (logged_in, msg) => {
			console.log(logged_in); // return a Boolean (true/false) if logged in.
			})
			//Test Admin Part
			application.login('https://yourpanelhostname/', APIKEYADMIN , (logged_in, msg) => {
			console.log(logged_in); // return a Boolean (true/false) if logged in.
			})
	```

