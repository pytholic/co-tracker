build:
    docker build -t pytholic/cotracker .

run:
    docker run \
    --name cotracker \
    --ipc=host \
    --gpus all \
    --privileged \
    -v /tmp/.X11-unix:/tmp/.X11-unix:rw \
    -v $HOME/.Xauthority:$HOME/.Xauthority \
    -e XAUTHORITY=$HOME/.Xauthority \
    -e DISPLAY=$DISPLAY \
    -it pytholic/cotracker