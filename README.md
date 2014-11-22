ssh-port-forwarding-ref
=======================

Quick reference of ssh port forward commands -- because I can never seem to remember...


## Network diagram:
```
  near-host   <--->   this-box   <--->   remote-box   <--->   far-host
  (4.3.2.1)           (1.2.3.4)          (5.6.7.9)            (9.8.7.6)
```

##### Make service running at remote-box:3000 available at this-box:3001

```bash
# All equivelent:
ssh -L 1.2.3.4:3001:5.6.7.9:3000 user@remote-box -N
ssh -L this-box:3001:remote-box:3000 user@remote-box -N
```

##### Make service running at far-host:80 available at this-box:5000

```bash
ssh -L this-box:5000:far-host:80 user@remote-box -N
```

##### Make service running at near-host:443 available at remote-box:4000

```bash
ssh -R remote-box:4000:near-host:443 user@remote-box -N
```


### Ports within the same host:

##### Make service running at this-box:3000 available at this-box:3005

```bash
# All equivelent:
ssh -L this-box:3005:this-box:3000 user@this-box -N
ssh -L 1.2.3.4:3005:1.2.3.4:3000 user@localhost -N
```

##### Make service running at remote-box:5000 available at remote-box:5010

```bash
# All equivelent:
ssh -R remote-box:5010:remote-box:5000 user@remote-box -N
ssh -R 5.6.7.9:5010:5.6.7.9:5000 user@5.6.7.9 -N
```

