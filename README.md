# am_rosdistro
AutoModality's extension of rosdistro private packages not eligible for merging

## Usage

Intended as an extension to the standard [rosdep](http://wiki.ros.org/rosdep), the files provided cause no conflict
and are to be delivered after `rosdep init` (prerequisite) and will be updated with `rosdep update`.

```
sudo curl https://raw.githubusercontent.com/AutoModality/am_rosdistro/main/rosdep/sources.list.d/10-automodality.list --output /etc/ros/rosdep/sources.list.d/10-automodality.list
rosdep update
```

confirm private package can be found:

```
rosdep resolve acsl_sdk
```

Expect similar to:

```
#apt
ros-melodic-acsl-sdk
```


## Adding new packages

Private packages not found when declared in `package.xml` will lead you to declare the associated debian package that will install 
ROS package.  Simply add the entry to the associated Ubuntu disto:

```
acsl_sdk:
  ubuntu:
    xenial: [ros-melodic-acsl-sdk]
```

Commit directly to master.  Run `rosdep update` and `rosdep resolve {package}` to confirm the debian artifact is provided.
