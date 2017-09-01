# arm32v7 docker piwik

To deploy to Scaleway C1:

docker-machine create -d scaleway \
  --scaleway-commercial-type "C1" \
  --scaleway-region "par1" \
  --scaleway-name piwik \
  --scaleway-image jessie \
  piwik

eval $(docker-machine env piwik)

docker build .
