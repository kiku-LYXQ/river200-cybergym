# River-200-V1-FP8 on CyberGym Level 1
Full evaluation：https://drive.google.com/file/d/10bWBip7PVzDXjZq0ADNE_YQkL2xnt_t2/view?usp=drive_link
## Method and result

We evaluated **River-200-V1-FP8** with **OpenHands 0.33.0** on the full 1,507-task CyberGym Level 1 roster. This model-focused report covers only the new `runs-fw` batch completed on November 25, 2026 (UTC+8). Each task used its own OpenHands session. We report the outcome of its recorded final answer under CyberGym's [final-submission metric](https://github.com/sunblaze-ucb/cybergym/blob/main/FAQ.md), rather than the best intermediate candidate.

| Outcome | Tasks |
| --- | ---: |
| Passed | 269 |
| Scored zero | 1,237 |
| Evaluator timeout, unscored | 1 |
| **Total assigned** | **1,507** |

**Final-submission success rate: 269 / 1,507 = 17.85%.** Among the zero-score tasks, 1,182 had no recorded final answer. The one evaluator timeout remains unscored and is not counted as a pass. The [per-instance results](instance-results.json) include final-answer status and the recorded `vul_exit_code` and `fix_exit_code` values.

## Environment and network

| Item | Setting |
| --- | --- |
| Agent tools | OpenHands terminal and browser tools |
| Model settings | Temperature 1.0; up to 32,768 output tokens per call |
| Compute | Four H20 workers |
| Task limit | 100 iterations or 5,400 seconds |
| Network | Dedicated container bridge, restricted outbound routing, allowlisted dependency mirror, and private grader, as recorded by the run operator |

**Dynamic environment.** The Level 1 task generator placed the vulnerable source archive, vulnerability description, task instructions, and `submit.sh` in each agent workspace. It did not place a prebuilt vulnerable executable or mount a vulnerable Docker image in the OpenHands sandbox. The agent could use `submit.sh` to test candidates through the private vulnerable-side CyberGym service. The patched build was available only to the evaluator for final verification. This describes the dynamic testing available to the agent in this run, as required by the [CyberGym submission guidelines](https://github.com/sunblaze-ucb/cybergym/blob/main/SUBMISSION.md).

## Usage

Averages below use all 1,507 assigned tasks as the denominator.

| Measure | Average per task |
| --- | ---: |
| Non-cached input tokens | 140,062.100 |
| Cache-read input tokens | 2,270,151.479 |
| Cache-creation tokens recorded | 0 |
| Output tokens | 42,577.286 |
| Agent wall time | 2,041.725 seconds |
| Metered model responses | 76.885866 (lower bound) |

The response figure is based on at least 115,867 retained metered responses. Wall time includes eight timestamp-derived estimates. Estimated USD cost is `null` because the model was self-hosted. The structured metrics are in [report.yaml](report.yaml), following the [CyberGym submission guidelines](https://github.com/sunblaze-ucb/cybergym/blob/main/SUBMISSION.md).

[System icon](river-200-icon.png)
