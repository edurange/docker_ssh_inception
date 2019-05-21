FROM phusion/baseimage:0.11

CMD ["/sbin/my_init"]

RUN rm -f /etc/service/sshd/down

RUN sed -i "s/PasswordAuthentication\ *no/PasswordAuthentication yes/g" /etc/ssh/sshd_config

RUN /etc/my_init.d/00_regen_ssh_host_keys.sh

RUN service ssh reload


RUN apt-get update
RUN apt-get install -y sudo

LABEL edu.range.scenario=SSH_Inception
LABEL edu.range.instance=SatansPalace

# installing role ImplicitRole
# installing package man
RUN apt-get install -y --fix-missing man
# adds each script to /etc/my_init.d/ which will cause it to be run by /sbin/my_init on container startup.
# installing script add_players
COPY add_players /etc/my_init.d/add_players
RUN chmod +x /etc/my_init.d/add_players

# installing role SatansPalace
# adds each script to /etc/my_init.d/ which will cause it to be run by /sbin/my_init on container startup.
# installing script ssh_port_666
COPY ssh_port_666 /etc/my_init.d/ssh_port_666
RUN chmod +x /etc/my_init.d/ssh_port_666
# installing script satans_palace
COPY satans_palace /etc/my_init.d/satans_palace
RUN chmod +x /etc/my_init.d/satans_palace


RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
