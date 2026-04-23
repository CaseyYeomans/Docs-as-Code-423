# CoreDNS Entry for Deployments

In some environments, DNS queries may unnecessarily leave the cluster to be resolved outside, which may result in massive delays or lookup failures. In order to improve DNS resolution in the cluster and avoid this scenario, it is *highly recommended* that a **CoreDNS** server be added. This server will resolve DNS queries that are meant for your Profisee environment's hostname (ex. *profiseedev.yourdomain.com*) to the Nginx ingress controller.

To add a **CoreDNS** entry:

1. Navigate to your Web portal > Cluster > Configuration.
2. Switch the **Filter by namespace** setting to **kube-system**, then edit the **coredns-custom** entry.

Do not edit the *coredns* entry. Only edit the *coredns-custom* entry.

3. If there is a **data:** section, please contact Profisee Support before implementing this change. If there is not a **data:** section, you may proceed with the next steps.

The following diagram shows a coredns-custom entry that does not have a **data:** section.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i33969c5ef66ff5e9.png)

The following image shows an entry that does have a **data:** section. If your entry resembles this, read below to determine if you already have the correct DNS entry.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i9b53d2af3c49093b.png)

Click **YAML** and copy and edit the entry below. See the above image for how the entry should appear.

This creates a **DNS server**. The name can be anything, but it must end in *.server*. If you prefer to keep the entries below stored somewhere, you can name them *ProfiseeDev.server*, *ProfiseeTest.server,* etc. Change the **YourHostName** section to match your domain name. For example, *profiseedev.yourdomain.com* should replace *YourHostName*:

```
data:
Profisee.server: |
YourHostName:53 {
rewrite name YourHostName nginx-ingress-nginx-controller.profisee.svc.cluster.local
kubernetes cluster.local in-addr.arpa ip6.arpa {
pods insecure
fallthrough in-addr.arpa ipv6.arpa
ttl 30
}
}
```

**Dev Example**

```
data:
ProfiseeDev.server: |
profiseedev.yourdomain.com:53 {
rewrite name profiseedev.yourdomain.com nginx-ingress-nginx-controller.profisee.svc.cluster.local
kubernetes cluster.local in-addr.arpa ip6.arpa {
pods insecure
fallthrough in-addr.arpa ipv6.arpa
ttl 30
}
}
```

**Test Example**

```
data:
ProfiseeTest.server: |
profiseetest.yourdomain.com:53 {
rewrite name profiseeteset.yourdomain.com nginx-ingress-nginx-controller.profisee.svc.cluster.local
kubernetes cluster.local in-addr.arpa ip6.arpa {
pods insecure
fallthrough in-addr.arpa ipv6.arpa
ttl 30
}
}
```

**Production Example**

```
data:
Profisee.server: |
profisee.yourdomain.com:53 {
rewrite name profisee.yourdomain.com nginx-ingress-nginx-controller.profisee.svc.cluster.local
kubernetes cluster.local in-addr.arpa ip6.arpa {
pods insecure
fallthrough in-addr.arpa ipv6.arpa
ttl 30
}
}
```

Once you add the **data:** section:

1. Save the **coredns-custom** entry.
2. Return to the cluster, then go to **Workloads**, then **Pods**.
3. Filter again by **kube-system.**
4. Sort by **Name** to find the two or more pods named *coredns-xxxxxxxxx-xxxxx* (not the *coredsn-autoscaler-xxxxxxxxxx-xxxxx).*
5. Select the above pods and click **delete**. They will be recreated immediately and will pick up the new config map change.

We recommend performing tests to determine if queries have yielded improvements. Monitor how long workflows take, login times, log noise, etc.