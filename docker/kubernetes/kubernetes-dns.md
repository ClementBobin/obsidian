Here’s your **Kubernetes DNS Cheat-Sheet** formatted for Obsidian:

---

# 🌐 Kubernetes DNS

## 🏷️ DNS for Services and Pods

Kubernetes automatically creates DNS records for Services and Pods, enabling you to access them with consistent DNS names instead of using IP addresses.

### Service DNS Format:

```
your-service.your-namespace.svc.cluster.local
```

### Pod DNS Format (Exposed via a Service):

```
your-prod.your-service.your-namespace.svc.cluster.local
```

---

## 🛠️ Custom DNS Settings

### 📝 Edit CoreDNS ConfigMap

To customize DNS settings, you can edit the `Corefile` section in the `configmap/coredns` in the `kube-system` namespace.

```yml
.:53 {
  # Existing config...
}
import /etc/coredns/custom/*.server
```

### ➕ Add a New ConfigMap

To use a custom DNS server (e.g., `clcreative.home`), create a ConfigMap with the following example:

```yml
apiVersion: v1
kind: ConfigMap
metadata:
  name: coredns-custom
  namespace: kube-system
data:
  clcreative.server: |
    clcreative.home:53 {
      forward . 10.20.0.10
    }
```

---

## Tags 📚

`#kubernetes` `#dns` `#coredns` `#services` `#pods`

---

This cheat-sheet provides a quick reference for Kubernetes DNS management and custom configurations. Let me know if you need further clarification!