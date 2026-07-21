# User-Supplied Real-Robot Evidence

## Provenance

- Supplied directly by the user in the PaperSpine conversation on 2026-07-14 (Asia/Shanghai).
- Deployment site: 顺丰深圳.
- User's qualitative conclusion: the complete robot exhibited a clear and practically obvious improvement in action behavior.
- Status: **user-authoritative real-robot observation, pending raw-log and protocol verification for publication**.

## Reported Comparison

| Robot | Version | Duration | Efficiency (/h) | Double-grab rate | Reflow rate |
|---|---|---:|---:|---:|---:|
| BOT154 | `Flow-KTO_new_release_0624` | 60:00 | 887 | 4.2% | 9.4% |
| BOT154 | `MIST_package_release_0622` | 153:00 | 666 | 1.8% | 9.9% |
| BOT159 | `Flow-KTO_new_release_0624` | 77:13 | 1116 | 1.6% | 5.2% |
| BOT159 | `MIST_package_release_0622` | 90:00 | 895 | 1.0% | 6.6% |

The baseline rows did not repeat site and robot identifiers in the chat-formatted table. This record interprets each baseline row as belonging to the immediately preceding robot/site block; that mapping must be confirmed before publication.

## Directly Computable Differences

| Robot | Efficiency Difference | Relative Efficiency Difference | Double-grab Difference | Reflow Difference |
|---|---:|---:|---:|---:|
| BOT154 | +221/h | +33.2% | +2.4 percentage points | -0.5 percentage points |
| BOT159 | +221/h | +24.7% | +0.6 percentage points | -1.4 percentage points |

Relative efficiency differences are computed from the reported rates. No pooled rate, confidence interval, significance test, or event count is inferred because raw denominators were not provided.

## Interpretation Boundary

- The user reports a clear qualitative improvement in whole-robot action behavior; this is valid as a direct deployment observation, not as a statistical statement.
- Both reported efficiency comparisons favor Flow-KTO by 221 processed units per hour, subject to the exact metric definition and deployment comparability.
- Reflow rate is numerically lower for Flow-KTO on both robots. Whether lower is operationally better must be stated in the protocol.
- Double-grab rate is numerically higher for Flow-KTO on both robots. Its definition and desired direction are not yet recorded, so it is not labeled an improvement or regression.
- Durations differ between Flow-KTO and baseline runs. Hourly normalization does not by itself remove time-of-day, parcel-mix, operator, load, hardware, or software-version confounding.
- These are two robot-level comparisons, apparently one deployment window per version and robot. They do not yet establish variance, statistical significance, or broad generalization.

## Required Verification Before Manuscript Use

1. Define `efficiency`, `double-grab rate`, and `reflow rate`, including numerator, denominator, and whether higher or lower is better.
2. Confirm that each baseline row corresponds to the same robot and site shown above.
3. Map deployment names to exact training checkpoints, reference checkpoints, configs, and code/data versions.
4. Record run dates/times, parcel mix or workload, operator/hardware settings, and whether the comparison was randomized, interleaved, or sequential.
5. Provide raw event counts or dashboard exports so rates and denominators can be independently recomputed.
6. State whether any other controller, perception, speed, preprocessing, or deployment setting changed between versions.
7. Add repeated windows or more robots before claiming robustness or broad real-world improvement.
