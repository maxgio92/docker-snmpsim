# SNMP Simulator

This docker image starts up snmpsim.

The UDP port `1161` should be mapped to the desired SNMP port.

By default this image contains an snmpwalk from `demo.snmplabs.com` under community name `demo`.

To use your own snmpwalks you should mount a folder with snmpwalks like this:

    docker run -v /somewhere/with/snmpwalks:/usr/local/snmpsim/data \
               -p 1161:1161/udp \
               tandrup/snmpsim

The filename determines the SNMP community name.

If you want to run snmpsimd with more flags then you can use `EXTRA_FLAGS`, like this:

    docker run -v /somewhere/with/snmpwalks:/usr/local/snmpsim/data \
               -p 1161:1161/udp \
               -e EXTRA_FLAGS="--v3-user=testing --v3-auth-key=testing123"
               tandrup/snmpsim
