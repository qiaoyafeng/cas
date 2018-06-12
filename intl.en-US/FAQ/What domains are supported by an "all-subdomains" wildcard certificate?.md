# What domains are supported by an "all-subdomains" wildcard certificate? {#concept_fvw_grp_ydb .concept}

Wildcard certificates only secure subdomains that are on the same level as the \* \(asterisk\) character.

For example, a wildcard certificate for \*.example.com works for domains such as abc.example.com, but not for subordinate domains like mycard.good.example.com.

Similarly, a wildcard certificate for \*.good.example.com works for domains such as mycard.good.example.com and mycalc.good.example.com

.

Currently, the all-subdomains certificates only support one wildcard domain.

