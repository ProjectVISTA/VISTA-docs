# 🛠️ What Debugs to Take

## IKE Site to Site VPN:
<pre>
di de reset
di de di
di vpn ike log filter rem-addr4/dst-addr4 'peer IP'
di de app ike -1
di de cons time en
di de en
</pre>
!!! info "For certificate authentication, include:"
<pre>di de app fnbamd -1</pre>

---

## IKE Remote Access (Dial-Up) Radius/LDAP:
<pre>
di de reset
di de di
di vpn ike log filter rem-addr4/dst-addr4 'peer IP'
di de app ike -1
di de app fnbamd -1
di de en
</pre>

!!! info "In case of ikev2 + local authentication, add: "
<pre>di de app eap_proxy -1</pre>

---

## IKE SAML
<pre>
di de reset
di de di
di vpn ike log filter rem-addr4/dst-addr4 'peer IP'
di de app ike -1
di de app samld -1
di de app fnbamd -1
di de app eap_proxy -1
di de app authd 7
di de en
</pre>

---

## To disable debugging:
Wait for a delete/negotiation failure message, and then:
<pre>
di de di
di de reset
</pre>

---

