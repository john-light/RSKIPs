** This document is a draft pre-RSKIP for consideration in the next RSK hard fork **

| RSKIP         | X                                |
| :------------ |:---------------------------------|
|**Title**      | Expanding the emergency multisig |
|**Created**    | JUL-2021                         |
|**Author**     | John Light                       |
|**Purpose**    | Sec                              |
|**Layer**      | Core                             |
|**Complexity** | 2                                |
|**Status**     | Draft                            |

## Background

In the Iris hard fork, the RSK community has adopted RSKIP-201, which institutes a 3-of-4 emergency multisig with a one-year timelock in case of inactivity by a quorum of PowHSM nodes (henceforth, "the Iris multisig"). RSKIP-201 intends to ensure the availability of funds in case a quorum of PowHSM nodes goes offline for an extended period of time due to hardware failure, software bug, or some other issue. While RSKIP-201 does provide a backup option in case of Powpeg failure, it opens up new attack vectors due to the difference in security models between the Powpeg and the Iris multisig.  

## Proposal

We propose to modify and expand the Iris multisig so that it is a 7-of-12 multisig, in line with the 7-of-12 PowHSM nodes required to operate the Powpeg. Emergency multisig signers will each be required to keep their private key in separate national legal jurisdictions and geographies to minimize the risk of coordinated attacks and natural disasters. The emergency multisig signers should also be a totally separate group of entities from the PowHSM operators.

## Implementation

Change the Iris emergency multisig to a 7-of-12 multisig. Ensure that no PowHSM operators are also emergency multisig signers, and that each emergency multisig signer is in a separate national legal jurisdiction and geography.

## Alternatives considered

**Removing the emergency multisig**  

This option was considered because there are some in the community who feel that having no emergency multisig is preferrable to having the Iris emergency multisig. We decided that, while we recognize the shortcomings of the Iris multisig, we would rather work to improve it rather than un-do the consensus that was formed for implementing the Iris multisig in the Iris hard fork.  

**A backup Powpeg**  

With this option, in case of a failure of the primary PowHSM nodes, the funds held in the Powpeg multisig would be sent to a multisig controlled by backup PowHSM nodes. These backup PowHSM nodes would be stored offline until they are needed in case of emergency, thus protecting them from wear and tear and potential disasters such as an electromagnetic pulse. The backup PowHSM nodes would also be run by a different set of entities in different national legal jurisdictions and geographies than the primary PowHSM nodes. 

The main downside of this approach is that if the primary PowHSM nodes fail due to hardware or software issues, the backup PowHSM nodes might be vulnerable to the same issue and fail as well. This could be mitigated by using a heterogenous hardware and software stack, consisting of different hardware from different manufacturers and a different implementation of the software used to operate the PowHSM nodes. However this will take more time to research and consider the costs and tradeoffs involved in this approach.

**Conclusion**  

Having considered these alternatives, we decided to settle on a simple expansion of the emergency multisig to increase the number of signatures required as a way of improving redundancy and raising the cost of an attack.
