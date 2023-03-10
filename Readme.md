Algorithm for deploying services in a group due to the given cost for best average response time.

## How to run

1. install python3
2. `pip3 install -r requirements.txt`
3. prepare your data. change the parameters in the `main` function of `main.py`

## Data structure for input and output

> Follow the comments in the `main` function of `main.py` to organize your data in files

### Functions 对应的func_obj



```json
{
  "index": 0,    # index in given function list
  "svcIndex": 0, # index of the service
  "input": 0,    # input data size
  "output": 0    # output data size
}
```

### Function chains 对应的chains

A dict describes the service dependencies



```json
{
  ${caller function index}: {
    ${called function index}: 3.2,    # each function may depend on many other functions with call coefficient
    ...
  },
	...
}
```

### Ability Constraints

A dict describes how many requests of each function should be solved **considering call coefficients** between functions

```json
{
  ${function index}: 0,
  ...
}
```

### User requirements	对应的users

```json
{
  ${server index}: {
    ${function index}: 0,
    ...
  },
  ...
}
```

### Services	对应svc_objs

```json
{
  "index": 0,    # index in given service list
  "res": {
  	"cpu": 0,
  	"ram": 0
  },
  "ability": 0,  # throughput with given resource
  "id": id       # unique service id. Not necessary in the algorithm
}
```

### Servers 对应node_objs

```json
{
  "index": 0,    # index in given node list
  "res": {
    "cpu": 0,
    "ram": 0
	}
}
```

### Server Connections	对应connections

```json
{
  ${fromIndex}: {
    ${toIndex}: {
      "delay": 0,
      "bandwidth": 0
    }
  }
}
```

### Price	对应prices

```json
{
  'cpu': 0.0,
  'ram': 0.0,
  'max': 0.0
}
```



### 			对应chains_list

## Input

```json
{
  "svcList": [services],
  "funList": [functions],
  "funChains": chains,
  
  "nodeList": [servers],
  "connections": [connections],
  
  "users": user requirements,
  "abilityConstraints": ability constraints
}
```
