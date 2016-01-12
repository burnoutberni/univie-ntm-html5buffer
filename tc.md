# tc commands

* http://www.linuxfoundation.org/collaborate/workgroups/networking/netem

Use ```change``` instead of ```add``` to change existing rules.

## latency

    sudo tc qdisc add dev wlp3s0 root netem delay 500ms

## bandwidth

    sudo tc qdisc add dev wlp3s0 handle 1: root htb default 11
    sudo tc class add dev wlp3s0 parent 1: classid 1:1 htb rate 1kbps
    sudo tc class add dev wlp3s0 parent 1:1 classid 1:11 htb rate 1kbps

## packet loss

    sudo tc qdisc add dev wlp3s0 root netem loss 0.1%

## clearing rules

    sudo tc qdisc del dev wlp3s0 root
