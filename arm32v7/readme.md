# arm32v7 docker piwik

To deploy to Scaleway C1:

    docker-machine create -d scaleway \
      --scaleway-commercial-type "C1" \
      --scaleway-region "par1" \
      --scaleway-name piwik \
      --scaleway-image jessie \
      piwik

    eval $(docker-machine env piwik)

The build phase takes some time due to building php from source
    docker build -t "arm32v7:piwik" .

    # Run a mysql instance with the name some-mysql
    docker run -d --name some-mysql -e MYSQL_ROOT_PASSWORD=MYSQL_ROOT_PASSWORD hypriot/rpi-mysql

    # Run a piwik instance that is linked to the mysql instance
    docker run -p9000:9000 -d -e MYSQL_ROOT_PASSWORD=MYSQL_ROOT_PASSWORD --link some-mysql:db -t "arm32v7:piwik"

    # Open a web browser to http://your-ip:9000/
    open http://$(docker-machine env piwik | grep HOST | awk -F'[/:]' '{print $4}'):9000
