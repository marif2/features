# v1.5.0 (draft)

[Documentation](http://kubernetes.github.io) & [Examples](http://releases.k8s.io/release-1.5/examples)

## Major Themes

- Improved Federation Support
  - Daemonsets
  - Deployments
  - ConfigMaps
- Simplified Cluster Deployment
  - Improvements to `kubeadm`
  - New command: `kubefed`
  - HA Setup for Master
- Node Robustness
  - Windows Server Container support
  - CRI implementation
  - `kubelet` API supports authentication and authorization

## Features

Features for this release were tracked via the use of the [kubernetes/features](https://github.com/kubernetes/features) issues repo.  Each Feature issue is owned by a Special Interest Group from [kubernetes/community](https://github.com/kubernetes/community)

- **Apps**
  - [stable] When replica sets cannot create pods, they will now report detail via the API about the underlying reason ([kubernetes/features#120](https://github.com/kubernetes/features/issues/120))
  - [stable] `kubectl apply` is now able to delete resources you no longer need with `--prune` ([kubernetes/features#128](https://github.com/kubernetes/features/issues/128))
  - [beta] Deployments that cannot make progress in rolling out the newest version will now indicate via the API they are blocked ([docs](https://deploy-preview-1699--kubernetes-io-vnext-staging.netlify.com/docs/user-guide/deployments/#failed-deployment)) ([kubernetes/features#122](https://github.com/kubernetes/features/issues/122))
  - [beta] StatefulSets allow workloads that require persistent identity or per-instance storage to be created and managed on Kubernetes. ([docs](https://deploy-preview-1719--kubernetes-io-vnext-staging.netlify.com/docs/concepts/abstractions/controllers/statefulsets/)) ([kubernetes/features#137](https://github.com/kubernetes/features/issues/137))
  - [beta] In order to preserve safety guarantees the cluster no longer force deletes pods on un-responsive nodes and users are now warned if they try to force delete pods via the CLI. ([dos](https://deploy-preview-1774--kubernetes-io-vnext-staging.netlify.com/docs/tasks/manage-stateful-set/scale-stateful-set/)) ([kubernetes/features#119](https://github.com/kubernetes/features/issues/119))
- **Auth**
  - [alpha] Further polishing of the Role-based access control alpha API including a default set of cluster roles. ([docs](http://kubernetes.io/docs/admin/authorization/)) ([kubernetes/features#2](https://github.com/kubernetes/features/issues/2))
  - [beta] Added ability to authenticate/authorize access to the Kubelet API ([docs](https://deploy-preview-1684--kubernetes-io-vnext-staging.netlify.com/docs/admin/kubelet-authentication-authorization/)) ([kubernetes/features#89](https://github.com/kubernetes/features/issues/89))
- **AWS**
  - [stable] Roles should appear in kubectl get nodes ([kubernetes/features#113](https://github.com/kubernetes/features/issues/113))
- **Cluster Lifecycle**
  - [alpha] Improved UX and usability for the kubeadm binary that makes it easy to get a new cluster running. ([docs](https://deploy-preview-1684--kubernetes-io-vnext-staging.netlify.com/docs/getting-started-guides/kubeadm/)) ([kubernetes/features#11](https://github.com/kubernetes/features/issues/11))
- **Cluster Ops**
  - [alpha] Added ability to create/remove clusters w/highly available (replicated) masters on GCE using kube-up/kube-down scripts. ([docs](https://deploy-preview-1810--kubernetes-io-vnext-staging.netlify.com/docs/admin/ha-master-gce/)) ([kubernetes/features#48](https://github.com/kubernetes/features/issues/48)) 
- **Federation**
  - [beta] Support for config maps in federation. ([docs](https://deploy-preview-1838--kubernetes-io-vnext-staging.netlify.com/docs/user-guide/federation/configmap/)) ([kubernetes/features#105](https://github.com/kubernetes/features/issues/105))
  - [alpha] Alpha level support for Daemonsets in federation. ([docs](https://deploy-preview-1827--kubernetes-io-vnext-staging.netlify.com/docs/user-guide/federation/daemonsets/)) ([kubernetes/features#101](https://github.com/kubernetes/features/issues/101))
  - [alpha] Alpha level support for Deployments in federation. ([docs](https://deploy-preview-1828--kubernetes-io-vnext-staging.netlify.com/docs/user-guide/federation/deployment/)) ([kubernetes/features#100](https://github.com/kubernetes/features/issues/100))
  - [alpha] Cluster federation: Added support for DeleteOptions.OrphanDependents for federation resources. ([docs](https://deploy-preview-1787--kubernetes-io-vnext-staging.netlify.com/docs/user-guide/federation/#cascading-deletion)) ([kubernetes/features#99](https://github.com/kubernetes/features/issues/99))
  - [alpha] Introducing `kubefed`, a new command line tool to simplify federation control plane deployment and cluster registration/deregistration experience. ([docs](https://deploy-preview-1822--kubernetes-io-vnext-staging.netlify.com/docs/admin/federation/kubefed/)) ([kubernetes/features#97](https://github.com/kubernetes/features/issues/97))
- **Network**
  - [stable] Services can reference another service by DNS name, rather than being hosted in pods ([kubernetes/features#33](https://github.com/kubernetes/features/issues/33))
  - [beta] Opt in source ip preservation for Services with Type NodePort or LoadBalancer ([docs](https://deploy-preview-1841--kubernetes-io-vnext-staging.netlify.com/docs/tutorials/services/source-ip/)) ([kubernetes/features#27](https://github.com/kubernetes/features/issues/27))
- **Node**
  - [alpha] Added ability to preserve access to host userns when userns remapping is enabled in container runtime ([kubernetes/features#127](https://github.com/kubernetes/features/issues/127))
  - [alpha] Introducing the v1alpha1 CRI API to allow pluggable container runtimes; an experimental docker-CRI integration is ready for testing and feedback. ([docs](https://github.com/kubernetes/community/blob/master/contributors/devel/container-runtime-interface.md)) ([kubernetes/features#54](https://github.com/kubernetes/features/issues/54))
  - [alpha] Kubelet launches container in a per pod cgroup hiearchy based on quality of service tier ([kubernetes/features#126](https://github.com/kubernetes/features/issues/126))
  - [beta] Kubelet integrates with memcg notification API to detect when a hard eviction threshold is crossed ([kubernetes/features#125](https://github.com/kubernetes/features/issues/125))
  - [beta] Introducing the beta version containerized node conformance test gcr.io/google_containers/node-test:0.2 for users to verify node setup. ([docs](https://deploy-preview-1784--kubernetes-io-vnext-staging.netlify.com/docs/admin/node-conformance/)) ([kubernetes/features#84](https://github.com/kubernetes/features/issues/84))
- **Scheduling**
  - [alpha] Added support for accounting opaque integer resources. ([docs](https://deploy-preview-1783--kubernetes-io-vnext-staging.netlify.com/docs/user-guide/compute-resources/#opaque-integer-resources-alpha-feature)) ([kubernetes/features#76](https://github.com/kubernetes/features/issues/76))
  - [beta] PodDisruptionBudget has been promoted to beta, can be used to safely drain nodes while respecting application SLO's ([docs](https://deploy-preview-1789--kubernetes-io-vnext-staging.netlify.com/docs/tasks/administer-cluster/safely-drain-node/)) ([kubernetes/features#85](https://github.com/kubernetes/features/issues/85))
- **UI**
  - [stable] Dashboard UI now shows all user facing objects and their resource usage. ([docs](https://deploy-preview-1793--kubernetes-io-vnext-staging.netlify.com/docs/user-guide/ui/)) ([kubernetes/features#136](https://github.com/kubernetes/features/issues/136))
- **Windows**
  - [alpha] Added support for Windows Server 2016 nodes and scheduling Windows Server Containers ([docs](https://deploy-preview-1771--kubernetes-io-vnext-staging.netlify.com/docs/getting-started-guides/windows/)) ([kubernetes/features#116](https://github.com/kubernetes/features/issues/116))

## Known Issues

Populated via [v1.5.0 known issues / FAQ accumulator](https://github.com/kubernetes/kubernetes/issues/37134)

* kubectl --force deletion is breaking upgrade tests [#37117](https://github.com/kubernetes/kubernetes/issues/37117)
* CRI: pass full seccomp profile path to runtime [#36997](https://github.com/kubernetes/kubernetes/issues/36997)
* getDeviceNameFromMount() function doesn't return the volume path correctly when the volume path contains spaces [#37712](https://github.com/kubernetes/kubernetes/issues/37712)

## Notable Changes to Existing Behavior

* Node controller no longer force-deletes pods from the api-server. ([#35235](https://github.com/kubernetes/kubernetes/pull/35235), [@foxish](https://github.com/foxish))
  * For StatefulSet (previously PetSet), this change means creation of
    replacement pods is blocked until old pods are definitely not running
    (indicated either by the kubelet returning from partitioned state,
    deletion of the Node object, deletion of the instance in the cloud provider,
    or force deletion of the pod from the api-server).
    This helps prevent "split brain" scenarios in clustered applications by
    ensuring that unreachable pods will not be presumed dead unless some
    "fencing" operation has provided one of the above indications.
  * For all other existing controllers except StatefulSet, this has no effect on
    the ability of the controller to replace pods because the controllers do not
    reuse pod names (they use generate-name).
  * User-written controllers that reuse names of pod objects should evaluate this change.

* Allow anonymous API server access, decorate authenticated users with system:authenticated group ([#32386](https://github.com/kubernetes/kubernetes/pull/32386), [@liggitt](https://github.com/liggitt))
  * kube-apiserver learned the '--anonymous-auth' flag, which defaults to true. When enabled, requests to the secure port that are not rejected by other configured authentication methods are treated as anonymous requests, and given a username of 'system:anonymous' and a group of 'system:unauthenticated'. 
  * Authenticated users are decorated with a 'system:authenticated' group.
  * NOTE: anonymous access is enabled by default. If you rely on authentication alone to authorize access, change to use an authorization mode other than AlwaysAllow, or or set '--anonymous-auth=false'.

## Deprecations

* extensions/v1beta1.Jobs is deprecated, use batch/v1.Job instead ([#36355](https://github.com/kubernetes/kubernetes/pull/36355), [@soltysh](https://github.com/soltysh))
* The kubelet --reconcile-cdir flag is deprecated because it has no function anymore. ([#35523](https://github.com/kubernetes/kubernetes/pull/35523), [@luxas](https://github.com/luxas))
* Notice of deprecation for recycler [#36760](https://github.com/kubernetes/kubernetes/pull/36760)

## Action Required Before Upgrading

* batch/v2alpha1.ScheduledJob has been renamed, use batch/v2alpha1.CronJob instead ([#36021](https://github.com/kubernetes/kubernetes/pull/36021), [@soltysh](https://github.com/soltysh))
* PetSet has been renamed to StatefulSet.
  If you have existing PetSets, **you must perform extra migration steps** both
  before and after upgrading to convert them to StatefulSets. ([docs](https://deploy-preview-1704--kubernetes-io-vnext-staging.netlify.com/docs/tasks/manage-stateful-set/upgrade-pet-set-to-stateful-set/)) ([#35663](https://github.com/kubernetes/kubernetes/pull/35663), [@janetkuo](https://github.com/janetkuo))
* If you are upgrading your Cluster Federation components from v1.4.x, please update your `federation-apiserver` and `federation-controller-manager` manifests to the new version ([#30601](https://github.com/kubernetes/kubernetes/pull/30601), [@madhusudancs](https://github.com/madhusudancs))
* The deprecated kubelet --configure-cbr0 flag has been removed, and with that the "classic" networking mode as well.  If you depend on this mode, please investigate whether the other network plugins `kubenet` or `cni` meet your needs. ([#34906](https://github.com/kubernetes/kubernetes/pull/34906), [@luxas](https://github.com/luxas))
* New client-go structure, refer to kubernetes/client-go for versioning policy ([#34989](https://github.com/kubernetes/kubernetes/pull/34989), [@caesarxuchao](https://github.com/caesarxuchao))
* The deprecated kube-scheduler --bind-pods-qps and --bind-pods burst flags have been removed, use --kube-api-qps and --kube-api-burst instead ([#34471](https://github.com/kubernetes/kubernetes/pull/34471), [@timothysc](https://github.com/timothysc))
* If you used the [PodDisruptionBudget](http://kubernetes.io/docs/admin/disruptions/) feature in 1.4 (i.e. created `PodDisruptionBudget` objects), then **BEFORE**  upgrading from 1.4 to 1.5, you must delete all `PodDisruptionBudget` objects (`policy/v1alpha1/PodDisruptionBudget`) that you have created. It is not possible to delete these objects after you upgrade, and their presence will prevent you from using the beta PodDisruptionBudget feature in 1.5 (which uses `policy/v1beta1/PodDisruptionBudget`). If you have already upgraded, you will need to downgrade the master to 1.4 to delete the `policy/v1alpha1/PodDisruptionBudget` objects.

### Previous Releases Included in v1.5.0

TODO: this is a manual list for now

- [v1.4.0-beta.2](CHANGELOG.md#v150-beta2)
- [v1.4.0-beta.1](CHANGELOG.md#v150-beta1)
- [v1.5.0-alpha.2](CHANGELOG.md#v150-alpha2)
- [v1.5.0-alpha.1](CHANGELOG.md#v150-alpha1)
