**Proposal Category:** Economics

**Proposal Type:** #NetworkEconomics

**Author:** (name or Principal?)

**Author's organization**: ?

**Date:** May 5, 20201 (Timestamp?)

**Status:** Failed

**Summary: **

The proposal aims to update the ICP/XDR conversion rate in the NNS. The proposed rate reflects the current market value of ICP $XX as of May 5, 2021.

**Rationale:** TBD

**Areas Affected:** TBD

**Related Proposals:** None

**NNS Payload submitted:**

(
  vec {
    record {
      id = opt record { id = 1 };
      status = 1;
      topic = 2;
      ballots = vec {
        record { 1; record { vote = 1; voting_power = 249_914_442_162 } };
        record { 18; record { vote = 0; voting_power = 249_914_442_162 } };
      };
      proposal_timestamp_seconds = 1_620_214_697;
      reward_event_round = 0;
      failed_timestamp_seconds = 0;
      reject_cost_e8s = 1;
      latest_tally = opt record {
        no = 0;
        yes = 249_914_442_162;
        total = 251_913_757_700_197;
        timestamp_seconds = 1_620_214_697;
      };
      reward_status = 1;
      decided_timestamp_seconds = 0;
      proposal = opt record {
        url = "";
        action = opt variant {
          ExecuteNnsFunction = record {
            nns_function = 10;
            payload = blob "DIDL\01l\03\90\cb\8b\aa\01q\df\f5\81\a0\08x\d6\d5\da\c6\0fx\01\00\00@B\0f\00\00\00\00\00(\83\92`\00\00\00\00";
          }
        };
        summary = "Conversion Rate Update";
      };
      proposer = opt record { id = 1 };
      executed_timestamp_seconds = 0;
    };
  },
)
