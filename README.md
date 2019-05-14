pyScriptFoam
=============
My python scripts for OpenFOAM data post-processing.  

# Prerequisites

# lagrangian  
## ~~postLagrangian.py~~
~~A python script to process lagrangian data and get droplets' diameter or velocity radial distributions.~~  
This script has been merged to sprayCloud.    
## sprayCloud.py
A python script to read the lagrangian droplets data and output them to a Tecplot format file. It can also do post-process like radial profiles of droplet diameter at different axial locations and SMD distribution alongside axial direction.  
### Usage:
```
python3 sprayCloud.py [-parallel] [-latestTime] [-post] [-help]"
```
  -parallel:    process the parallel data  
  -latestTime:  only process the latestTime solution  
  -post:        post-process the droplet data  
  -help:        print this message  
### Eg:
This will read all parallel Lagrangian spray data and output them in Tecplot format. A folder name `Tecplot` will be created to save these files.  
```
python3 sprayCloud.py -parallel
```
This will only output the latestTimes's spray data in Tecplot format.  
```
python3 sprayCloud.py -parallel -latestTime
```
This will post-process parallel Lagrangian spray data and get profiles. A `postDict` should be given under `postSpray` folder, like this [example](https://github.com/TimoLin/pyScriptFoam/blob/master/lagrangian/postSpray/postDict).  
```
python3 sprayCloud.py -parallel -post
```

## sprayTrans.py
A python script to converte sprayCloud:rhoTrans__[liquidPhase] file (source term) into Tecplot readable OpenFOAM format(like T, U etc).  
A new file named: rhoTrans__[liquidPhase] will be generated.  
### Usage:  
```
python3 sprayTrans.py -liquid <phaseName> [-latestTime] [-parallel] [-help]
```
  -liquid <phaseName>: specific the liquid mixture name  
  -latestTime: only parse the latest solution  
  -parallel:   parse the parallel data  
  -help:       show this message  

### Eg:  
```
python3 sprayTrans.py -liquid C2H5OH -latestTime
```
