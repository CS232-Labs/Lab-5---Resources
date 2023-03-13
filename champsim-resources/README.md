# Champsim Resources

## Installation

```
    sudo docker pull cs232ta/champsim-docker:latest
    
    # For first time usage:
    sudo docker run --name cs232 -v <absolute-path-of-folder-in-your-machine>:/shared_folder -it cs232ta/champsim-docker


    # For further usage:
    sudo docker start cs232
    sudo docker exec -it cs232 /bin/bash
```

