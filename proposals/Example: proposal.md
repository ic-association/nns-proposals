
# 0-Proposal: Template

```
Proposal ID: 0
Proposal Topic: #ExchangeRate
Proposal Type: SetICPSDR
Proposal Type description: SetICPSDR: Instruct the NNS about the market value of 1 ICP as measured by an IMF SDR.
Author: 
Author's organization: 
Timestamp: 1620278127
Time: Thursday, May 6, 2021 5:15:17 AM GMT
Status: Failed
```

## Summary:

The proposal aims to update the ICP/XDR conversion rate in the NNS. This setting affects cycles pricing (as the value of cycles shall be constant with respect to IMF SDRs). The proposed rate reflects the current market value of ICP $XX. A new proposal of this type is expected to be submitted every 5 minutes.

## Rationale:

Market rate changed and it must be kept upto date in the NNS registry.

## Areas Affected:

The rate in the NNS Registry which consumes the rate to determine the rate between ICP and Cycles.

## Related Proposals:

None

**NNS Submitted:**
