# [OpenClassRooms_EvaluezLesPerformancesdUnModeleDeML](Evaluez les performances d'un modele de machine learning)
This is my course notes of "Evaluez les performances d'un modele de machine learning" in OpenClassrooms

## Note to set up docker
#### to build an image
```docker build -t <image name> .```

#### to run a container
```docker container run -it --name <container name> -p 5000:5000 -v ~/workspace/<working folder>:/workspace -d <image name>```

#### to execute the container in bash
```docker exec -it <container name> bash```

#### start jupyter notebook in the containter
```jupyter notebook --port=5000 --no-browser --ip=0.0.0.0 --allow-root```
