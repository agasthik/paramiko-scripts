### Utility Python Paramkio Scripts for Remote Server Management

##### [Review Installation Instructions](../master/Install%20Python%20Paramiko.md)

##### [Run The Sample Scripts](../master/infrachecks.py)
###### The [sample script](../master/infrachecks.py) needs the sample server [inventory file](../master/servernames.txt) as well.

Sample Execution is below. SERVERNAME1 and SERVERNAME2 are dummy names

```bash
$ ./infrachecks.py 

||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||
SERVERNAME-1
 INFRASTRUCTURE METRICS 
Memory >> Mem:          3821       2045       1775          0        470        648 
Number of Processors >> 1
||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||--||
SERVERNAME2
 INFRASTRUCTURE METRICS 
Memory >> Mem:          3821       2737       1083          0        567       1246 
Number of Processors >> 1
```
