# 🛠️ What Debugs to Take

## NP6:
<pre>
diagnose npu np6 dce 0
diagnose npu np6 dce 0
diagnose npu np6 dce 0
diagnose npu np6 dce 0
diagnose npu np6 dce 0
diagnose npu np6 pdq 0
diagnose npu np6 pdq 0
diagnose npu np6 pdq 0
diagnose npu np6 pdq 0
diagnose npu np6 hrx-drop 0
diagnose npu np6 hrx-drop 0
diagnose npu np6 hrx-drop 0
diagnose npu np6 hrx-drop 0
diagnose npu np6 hrx-drop 0
diagnose npu np6 anomaly-drop 0
diagnose npu np6 anomaly-drop 0
diagnose npu np6 anomaly-drop 0
diagnose npu np6 anomaly-drop 0
diagnose npu np6 anomaly-drop 0
diagnose npu np6 sse-stats 0
diagnose npu np6 sse-stats 0
diagnose npu np6 sse-stats 0
diagnose npu np6 sse-stats 0
diagnose npu np6 sse-stats 0
diagnose npu np6 xgmac-stats 0
diagnose npu np6 xgmac-stats 0
diagnose npu np6 xgmac-stats 0
diagnose npu np6 session-stats 0
diagnose npu np6 register 0
diagnose npu np6 register 1
diagnose npu np6 ipsec-stats
diagnose npu np6 ipsec-stats
diagnose npu np6 ipsec-stats
diagnose npu np6 ipsec-stats
diagnose npu np6 ipsec-stats
fnsysctl cat /proc/net/np6_0/ipsec-engine
fnsysctl cat /proc/net/np6_0/ipsec-engine
fnsysctl cat /proc/net/np6_0/ipsec-engine
fnsysctl cat /proc/net/np6_1/ipsec-engine
fnsysctl cat /proc/net/np6_1/ipsec-engine
fnsysctl cat /proc/net/np6_1/ipsec-engine
fnsysctl cat /proc/net/np6_0/gige-stats
fnsysctl cat /proc/net/np6_1/gige-stats
</pre>

---

## NP7:
<pre>
diagnose npu np7 dce-drop-all all
diagnose npu np7 dsw-drop-all all
diagnose npu np7 dsw-drop-all all
diagnose npu np7 dsw-drop-all all
diagnose npu np7 dsw-drop-all all
diagnose npu np7 cgmac-stats all
diagnose npu np7 cgmac-stats all
diagnose npu np7 cgmac-stats all
diagnose npu np7 cgmac-stats all
diagnose npu np7 cgmac-stats all
diagnose npu np7 hif-stats all
diagnose npu np7 hif-stats all
diagnose npu np7 hif-stats all
diagnose npu np7 hif-stats all
diagnose npu np7 hif-stats all
diagnose npu np7 hif-stats all
diagnose npu np7 dsw-drop-all
diagnose npu np7 dsw-drop-all
diagnose npu np7 dsw-drop-all
diagnose npu np7 dsw-drop-all
diagnose npu np7 dsw-drop-all
diagnose npu np7 pba all
diagnose npu np7 pba all
diagnose npu np7 pba all
fnsysctl cat /proc/net/np7/np7_0/pcie_latency
fnsysctl cat /proc/net/np7/np7_1/pcie_latency
fnsysctl cat /proc/net/np7/np7_2/pcie_latency
fnsysctl cat /proc/net/np7/np7_3/pcie_latency
fnsysctl cat /proc/net/np7/np7_4/pcie_latency
fnsysctl cat /proc/net/np7/np7_5/pcie_latency
fnsysctl cat /proc/net/np7/np7_0/pcie_latency
fnsysctl cat /proc/net/np7/np7_1/pcie_latency
fnsysctl cat /proc/net/np7/np7_2/pcie_latency
fnsysctl cat /proc/net/np7/np7_3/pcie_latency
fnsysctl cat /proc/net/np7/np7_4/pcie_latency
fnsysctl cat /proc/net/np7/np7_5/pcie_latency
diagnose npu np7 pdq all
diagnose npu np7 pdq all
diagnose npu np7 pdq all
diagnose npu np7 pdq all
diagnose npu np7 pdq all
diagnose npu np7 hpe all
diagnose npu np7 pmon all
diagnose npu np7 phy-status
diagnose npu np7 sse-stats all
diagnose npu np7 session-offload-stats all
fnsysctl cat proc/net/np7/sys_conf
fnsysctl cat proc/net/np7/tpe_tse
fnsysctl cat proc/net/np7/tpe_pshaper
fnsysctl cat /proc/np7_0/mse/drops
diagnose npu np7 ipl -v -M ALL_SSE
fnsysctl cat proc/net/np7/np7_0/tbl/cdb_spv_htab_csr_info
fnsysctl cat proc/net/np7/np7_0/tbl/cdb_tpv_htab_csr_info
fnsysctl cat proc/net/np7/np7_0/tbl/cdb_spact_tbl
fnsysctl cat proc/net/np7/np7_0/tbl/cdb_tpact_tbl
fnsysctl cat proc/net/np7/np7_1/tbl/cdb_spv_htab_csr_info
fnsysctl cat proc/net/np7/np7_1/tbl/cdb_tpv_htab_csr_info
fnsysctl cat proc/net/np7/np7_1/tbl/cdb_spact_tbl
fnsysctl cat proc/net/np7/np7_1/tbl/cdb_tpact_tbl
fnsysctl cat proc/net/np7/np7_2/tbl/cdb_spv_htab_csr_info
fnsysctl cat proc/net/np7/np7_2/tbl/cdb_tpv_htab_csr_info
fnsysctl cat proc/net/np7/np7_2/tbl/cdb_spact_tbl
fnsysctl cat proc/net/np7/np7_2/tbl/cdb_tpact_tbl
fnsysctl cat proc/net/np7/np7_3/tbl/cdb_spv_htab_csr_info
fnsysctl cat proc/net/np7/np7_3/tbl/cdb_tpv_htab_csr_info
fnsysctl cat proc/net/np7/np7_3/tbl/cdb_spact_tbl
fnsysctl cat proc/net/np7/np7_3/tbl/cdb_tpact_tbl
fnsysctl cat proc/net/np7/np7_4/tbl/cdb_spv_htab_csr_info
fnsysctl cat proc/net/np7/np7_4/tbl/cdb_tpv_htab_csr_info
fnsysctl cat proc/net/np7/np7_4/tbl/cdb_spact_tbl
fnsysctl cat proc/net/np7/np7_4/tbl/cdb_tpact_tbl
fnsysctl cat proc/net/np7/np7_5/tbl/cdb_spv_htab_csr_info
fnsysctl cat proc/net/np7/np7_5/tbl/cdb_tpv_htab_csr_info
fnsysctl cat proc/net/np7/np7_5/tbl/cdb_spact_tbl
fnsysctl cat proc/net/np7/np7_5/tbl/cdb_tpact_tbl
fnsysctl cat /proc/net/np7/np7_0/tpe
fnsysctl cat /proc/net/np7/np7_1/tpe
fnsysctl cat /proc/net/np7/np7_2/tpe
fnsysctl cat /proc/net/np7/np7_3/tpe
fnsysctl cat /proc/net/np7/np7_4/tpe
fnsysctl cat /proc/net/np7/np7_5/tpe
diagnose npu np7 sse-stats all
diagnose npu np7 dsw-ingress-stats all
diagnose npu np7 dsw-egress-stats all
diagnose npu np7 dsw-drop-by-src all
diagnose npu np7 dsw-drop-by-dst all
diagnose npu np7 session-offload-stats all
fnsysctl cat /proc/net/np7/ipsec_stat
diagnose npu np7 dce-ipsec-drop all
diagnose npu np7 pmon all
fnsysctl cat /proc/net/np7/qtm_stat
fnsysctl cat /proc/net/np7/qtm
diagnose npu np7 sw-np-que all
diagnose npu np7 msg sse-rate all
diagnose npu np7 listreg all
</pre>

!!! info "In case of ikev2 + local authentication, add: "
<pre>di de app eap_proxy -1</pre>

---

## NP6XLite
<pre>
diagnose npu np6xlite dce 0
diagnose npu np6xlite dce 0
diagnose npu np6xlite dce 0
diagnose npu np6xlite dce 0
diagnose npu np6xlite dce 0
fnsysctl cat /proc/net/np6xlite_0/pdq
fnsysctl cat /proc/net/np6xlite_0/pdq
fnsysctl cat /proc/net/np6xlite_0/pdq
fnsysctl cat /proc/net/np6xlite_0/pdq
fnsysctl cat /proc/net/np6xlite_0/pdq
diagnose npu np6xlite hpe 0
diagnose npu np6xlite hpe 0
diagnose npu np6xlite hpe 0
diagnose npu np6xlite anomaly-drop 0
diagnose npu np6xlite anomaly-drop 0
diagnose npu np6xlite anomaly-drop 0
diagnose npu np6xlite anomaly-drop 0
diagnose npu np6xlite anomaly-drop 0
diagnose npu np6xlite session-stats
diagnose npu np6xlite session-stats
diagnose npu np6xlite session-stats
diagnose npu np6xlite session-stats
diagnose npu np6xlite session-stats
fnsysctl cat /proc/net/np6xlite_0/hif-stats
fnsysctl cat /proc/net/np6xlite_0/hif-stats
fnsysctl cat /proc/net/np6xlite_0/hif-stats
fnsysctl cat /proc/net/np6xlite_0/hif-stats
fnsysctl cat /proc/net/np6xlite_0/hif-stats
fnsysctl cat /proc/net/np6xlite_0/hifdrop
fnsysctl cat /proc/net/np6xlite_0/hifdrop
fnsysctl cat /proc/net/np6xlite_0/hifdrop
diagnose npu np6xlite ipsec-fragment
diagnose npu np6xlite ipsec-fragment
fnsysctl cat /proc/net/np6xlite_0/ipt-stat
fnsysctl cat /proc/net/np6xlite_0/ipt-stat
fnsysctl cat /proc/net/np6xlite_0/ipt-stat
fnsysctl cat /proc/net/np6xlite_0/ipsec-perf
fnsysctl cat /proc/net/np6xlite_0/ipsec-perf
fnsysctl cat /proc/net/np6xlite_0/mibs/gige2
fnsysctl cat /proc/net/np6xlite_0/mibs/gige4
fnsysctl cat /proc/net/np6xlite_0/mibs/gige6
fnsysctl cat /proc/net/np6xlite_0/mibs/gige8
fnsysctl cat /proc/net/np6xlite_0/msg
fnsysctl cat /proc/net/np6xlite_0/ipsec-ob0
fnsysctl cat /proc/net/np6xlite_0/ipsec-ib0
fnsysctl cat /proc/net/np6xlite_0/osw
fnsysctl cat /proc/net/np6xlite_0/fos-perf
fnsysctl cat /proc/net/np6xlite_0/sse-hw
</pre>

---

## NP7Lite
<pre>
diagnose npu np7lite dce-drop-all 0
diagnose npu np7lite dce-drop-all 0
diagnose npu np7lite dce-drop-all 0
diagnose npu np7lite dce-drop-all 0
diagnose npu np7lite dce-drop-all 0
diagnose npu np7lite pba 0
diagnose npu np7lite pba 0
diagnose npu np7lite pba 0
diagnose npu np7lite pba 0
diagnose npu np7lite sse-stats 0
diagnose npu np7lite sse-stats 0
diagnose npu np7lite sse-stats 0
fnsysctl cat /proc/net/np7lite/np7lite_0/ipsec-perf
fnsysctl cat /proc/net/np7lite/np7lite_0/ipsec-perf
fnsysctl cat /proc/net/np7lite/np7lite_0/ipsec-perf
fnsysctl cat /proc/net/np7lite/np7lite_0/ipsec-perf
fnsysctl cat /proc/net/np7lite/np7lite_0/ipsec-perf
diag npu np7lite hif-stats 0
diag npu np7lite hif-stats 0
diag npu np7lite hif-stats 0
diag npu np7lite hif-stats 0
diag npu np7lite pmon-s
diag npu np7lite pmon-s
diag npu np7lite pmon-s
diag npu np7lite pmon-s
diag npu np7lite pmon-s
diag npu np7lite inf
diag npu np7lite port-list
diag npu np7lite phy-status
diag npu np7lite system-config
diag npu np7lite init-params
diagnose npu np7lite pmon
diagnose npu np7lite msg 0
diagnose npu np7lite dsw-qtbl-stats 0 verbose
diagnose npu np7lite dce-eng-drop 0 verbose
diagnose npu np7lite dce-dsw-drop 0 verbose
diagnose npu np7lite dce-eng-stats 0
fnsysctl cat /proc/net/np7lite/qtm
fnsysctl cat /proc/net/np7lite/np7lite_0/hif-stats
fnsysctl cat /proc/net/np7lite/np7lite_0/hif-que
fnsysctl cat proc/net/np7lite/np7lite_0/tse
fnsysctl cat /proc/net/np7lite/tpe
diag npu np7lite dce-l2p-drop 0 verbose
diag npu np7lite dce-hif-drop 0 v
diag npu np7lite mac-mibs
diag npu np7lite dce-ihp-drop 0 v
diag npu np7lite dce-msw-stats 0
diag npu np7lite dsw-buf-stats 0
diag npu np7lite mas
diag npu np7lite getreg 0 all max
diag npu np7lite listreg all max
diag npu np7lite listtbl all
diag npu np7lite readtbl all
diag npu np7lite hpe 0
fnsysctl cat /proc/net/np7lite/qtm
fnsysctl cat /proc/net/np7lite/np7lite_0/hif-que
fnsysctl cat /proc/net/np7lite/np7lite_0/hif-stats
fnsysctl cat /proc/net/np7lite/tpe
fnsysctl cat proc/net/np7lite/np7lite_0/tse
</pre>

---


