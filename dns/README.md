gcloud dns


gcloud dns managed-zones create --dns-name="superguacamole.com" --description "A zone for testing stuff" super-guacamole

gcloud dns managed-zones list

gcloud dns managed-zones describe super-guacamole



## Adding an A record 
gcloud dns record-sets transaction start -z=super-guacamole
gcloud dns record-sets transaction add -z=super-guacamole --name="superguacamole.com." --type=A --ttl=60 "35.197.255.132"
//Do more if you want 
gcloud dns record-sets transaction execute -z=super-guacamole 
