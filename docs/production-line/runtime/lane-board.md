# Lane Board

| lane | packet_id | worktree | branch | state | green_level_target | blocker_class | next_recovery_action | next_handoff_point | notes |
|---|---|---|---|---|---|---|---|---|---|
| control | d0-control-20260411-01 | `<target-root>` | main | ready | lane_green |  | keep delivery state current | Gate A review | standing control lane |
| provisioning | d0-provisioning-20260411-01 | `<target-root>` | main | drafted | gate_green |  | record provider, domain, username, and checker-key status | hardening packet issuance |  |
| hardening | d0-hardening-20260411-01 | `<target-root>` | main | drafted | gate_green |  | wait for provisioning facts and safe access path | Gate A review | main SSH/firewall lane |
| nginx | d0-nginx-20260412-01 | `<target-root>` | main | drafted | gate_green |  | wait for hardening lane | Gate B review |  |
| ssl | d0-ssl-20260413-01 | `<target-root>` | main | drafted | release_green |  | wait for HTTP baseline | Gate C review |  |
| proof | d0-proof-20260411-01 | `<target-root>` | main | ready | lane_green |  | append logs after each session | session handoff | standing proof lane |
