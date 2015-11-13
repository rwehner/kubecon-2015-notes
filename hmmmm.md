== To Think more about

There was a lot of great stuff, but these things made made me want to do a bit more research. In no particular order...

* New v1.1 things to implement:
    * [Ingress](https://github.com/kubernetes/kubernetes/blob/master/docs/user-guide/ingress.md) - Maybe this can save us from some of out F5 configuration problems.
    * Review resource over-commit framework (guaranteed, burstable, best effort). How should we specify this when creating our deployments? Where are the docs?
    * Move our 1.1 release to use iptables-based kube-proxy (`--proxy-mode="iptables"`)
    * Figure out "interactive" `kubectl` commands (`run`, `attach`, `edit`, `apply`)
    * Enable the `v1beta` API extensions, especially Jobs and Deployments.
    * Look at KubeDash to replace KubeUI.
* PaaS-like dev workflow seems intriguing for our desire to increase dev velocity and self-serve.
    * Talked to [Deis](https://github.com/deis/deis) people, ovrclk.com and OpenShift. Maybe some investigation in that area.
    * All seemed to be moving to Kubernetes, but not yet fully moved at this time. OpenShift released 3.1 at KubeCon.
    * Nice things in OpenShift that we want: LDAP integration, manifest templates, edge routing
* Calico and OpenContrail both seemed interesting if/when we have network issues. Probably delay looking into this until then.
    * OpenContrail _seems_ like it can build isolated networks based on Kubernetes manifests.
* TLS certificate management. Several different take on this in the talks:
    * Ebay: Look at cfssl and lemur (from Netflix)
    * from [tutorial](//github.com/philips/real-world-kubernetes). - Not production-hardened, but uses cfssl too
    * github.com/inquicker/kaws has another TLS setup implementation
* When Kubernetes cluster federation lands (Q1?), would it make blue/green cluster upgrades possible?
* [Prometheus](http://prometheus.io) has some buzz. 
    * How does it compare to Heapster/Grafana?
    * If easier to set up and configure, may be nice to try.
    * I get the impression that Graphite/Nagios isn't going to survive long in a Kubernetes world...
* containerbuddy.io - mentioned as possible help in getting legacy apps to register/use service discovery.
* Watch Lachlan's [Kubernetes talk](https://www.openstack.org/summit/tokyo-2015/videos/presentation/decomposing-lithiums-monolith-with-kubernetes-and-openstack) from OpenStack summit. Did not have time to demo at KubeCon.
* Monolith advice: just convert to a megapod, then refactor as that seems painful.
* [Jenkins on Kubernetes example](github.com/GoogleCloudPlatform/continuous-deployment-on-kubernete). Not production ready, but something to build from?
* Read `kubectl` docs again. Lots of new stuff or things I never saw (`--watch`).
* Run through the full https://github.com/philips/real-world-kubernetes tutorial.
    * Implement an Etcd backup strategy for our clusters. This need emphasized by Brandon.
    * Review the TLS certificate generation in this repo. Can we leverage that?
    * Mentioned on AWS/GKE that you can run one Etcd and offload HA to EBS.
    * `kubelet`'s `--pod-eviction-timeout` is off by default. Should investigate to see if this is what we want.
* Could OpenShift's [F5 work](https://github.com/openshift/origin-server/blob/master/routing-daemon/README.md#using-f5-big-ip-ltm) be used to help Kubernetes interface with our F5s on service changes.
* [NavOps](http://www.navops.io/) was a vendor there. If we ever want to go back to an RPM-based Kubernetes, that project may be interesting.
* github.com/inquicker/kaws also does user certificates (or tokens). See if we can learn something there.
* https://github.com/skippbox/skippbox - similar to other kubernetes-in-docker mini implementations, but could be useful.

== random
* "don't use static configs to track a dynamic infra."
* Use [Tinc](http://www.tinc-vpn.org/) for VPNs
