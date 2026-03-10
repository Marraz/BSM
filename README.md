# BSM
Ingress and organize blackmagicdesign devices clips and projects into your own server.

- [BSM](#bsm)
  - [Important nodes](#important-nodes)
  - [Enviroment variables](#enviroment-variables)
    - [STORAGE\_PATH](#storage_path)
    - [FREE\_SPACE\_THRESHOLD\_BYTES](#free_space_threshold_bytes)
    - [COMPENSATION\_HOURS](#compensation_hours)
    - [MAX\_JOB\_HISTORY](#max_job_history)
  - [Download](#download)
    - [Docker](#docker)
    - [Unraid](#unraid)
    - [Truenas](#truenas)
  - [TODO](#todo)

## Important nodes
- Currently atems are organize as \<STORAGE_PATH\>/\<Project_name\>/\<Date\>/\<Project\>/...\
Hyperdecks and cameras as \<STORAGE_PATH\>/\<Project_name\>/\<Date\>/\<Clip\> \
Note that for hyperdecks and cameras, the <Project_name> is consider the name of the clip until the first '_' to be compatible with clips with or without timestamp in the name.
- Open telemetry and prometheus (\<docker_ip:port\>\\metrics) is supported, most don't needed but feel free to use it if you like.

## Enviroment variables
### STORAGE_PATH
Default value: "/data/"
    Path used to store files

### FREE_SPACE_THRESHOLD_BYTES 
Default value: 536870912000
    How many space in bytes to reserver for the rest of the system, I recommend leaving a few gigabytes for proxy videos or any other needs
### COMPENSATION_HOURS
Default value: 0
    When organicing by date, individual clips from cameras or hyperdecks may be added to a folder under the next day when filming overnight, normally this is fine, but if you are using a Atem to sync your files and this is running over night too, Atem project is going to be organize into the folder when it started, this can be used to shift or move your timezone where the whole project would have been recorded on the same day. For example, you started recording at 10pm with an atem and some cameras, created many clips and ended at 3 am next day, by assigning -4 to this variable all your clips are going to be organize into the same date. Useful when this is a recurring scenario.
### MAX_JOB_HISTORY
Default value: 180
    Max number or days job history should be store.

## Download
### Docker
docker run -d -p 8080:8080 marraz/bsm:latest
Docker compose example in examples/docker-compose.yml

### Unraid
Template coming soon

### Truenas
Template coming soon

## TODO
- IP and model auto-detect
- Pause on recording
- Limit max number of workers
- Individual schedule per device or configure global scheduler for better compatibility with lower capacity systems
- Add mirror mode
