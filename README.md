# ocp4-power

Derived from https://github.com/ocp-power-automation/ocp4-playbooks/blob/master/playbooks/roles/ocp-customization/tasks/powervm_rmc.yaml.

Re-implemented to remove Ansible dependency tree and to templatize in order to be more generally applicable to wider use cases.

The only material change from the original implementation is that the dependency on the standard `scc/privileged` has been removed.  It is replaced by a use-case specific scc that can be tailored as needed.

# Deploy

    oc process -f deploy.yaml | oc create -f -

Template parameters that can be defined in `deploy.yaml` or added to the `oc process` command line:
1. NS - Target project and namespace.
2. SA - ServiceAccount name to create.
3. SCC - SecurityContextConstraint name to create.
4. DS - DaemonSet name to create.

All parameters values default to `powervm-rmc` but can overridden if there are naming standards needed for compliance.
