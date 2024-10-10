###################################
# Image name: wrfhydro/domaintesting:c5_3_0
# Author: Kevin Sampson <ksampson@ucar.edu>
# Date:  2024-10-10
###################################
FROM wrfhydro/dev:base

MAINTAINER kevin.sampson@airbornesnowobservatories.com
USER root

############################
#Get the entrypoint script to download the code release
COPY ./entrypoint.sh /.
RUN chmod 777 /entrypoint.sh

USER docker
WORKDIR /home/docker

############################
RUN /entrypoint.sh

############################
#Copy local setEnvar.sh script and compile WRF-Hydro using compile option 2
COPY ./setEnvar.sh /home/docker/wrf_hydro_nwm_public/trunk/NDHMS
RUN cd ./wrf_hydro_nwm_public/trunk/NDHMS && ./configure 2 && ./compile_offline_NoahMP.sh setEnvar.sh
WORKDIR /home/docker