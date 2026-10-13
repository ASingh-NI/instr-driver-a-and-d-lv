# Contributing to instr-driver-a-and-d-lv

Contributions to the A&D balance LabVIEW driver are welcome from all!

instr-driver-a-and-d-lv is managed via [git](https://git-scm.com), with the canonical upstream
repository hosted on [GitHub](https://github.com/ASingh-NI/instr-driver-a-and-d-lv/).

instr-driver-a-and-d-lv follows a pull-request model for development. To contribute, create a
GitHub account, fork this project, push a branch with your changes to your fork, and
then submit a pull request.

Please sign off your commits (e.g. `git commit -s`). This adds a line of the form
`Signed-off-by: Name Lastname <name.lastname@example.com>` to the commit message,
indicating that you have read and agree to the Developer Certificate of Origin (see
below). Include a `Signed-off-by` line for every author of a commit.

See [GitHub's documentation](https://docs.github.com/pull-requests) for more details.

# Getting Started

1. Install the prerequisites:
   - LabVIEW, using the **oldest LabVIEW version `A&D.llb` is saved in**. Do not save
     the VIs in a newer version.
   - [NI-VISA](https://www.ni.com/en/support/downloads/drivers/download.ni-visa.html)
     and NI MAX.
   - LabVIEW VI Analyzer Toolkit.
2. Fork this repository and clone your fork.
3. Create a topic branch, e.g. `git checkout -b users/<name>/a-and-d-<change>`.
4. Copy the `A&D/` folder to `<LabVIEW>\instr.lib\` and mass compile it. There should be
   no broken VIs before you start.

# Making Changes

- This is a non-project-style driver: all VIs live in `A&D.llb`. Keep new VIs in the LLB
  and use the `A&D ` name prefix.
- Follow the LabVIEW Plug and Play driver structure (Initialize, Action/Status, Data,
  Utility, Close) and the 4-2-2-4 connector pane with **VISA resource name** and
  **error in/error out** in the standard terminals.
- Keep serial communication settings (port, baud rate, parity, termination, timeout)
  on `A&D Initialize.vi`; other VIs should reuse the open session.
- State in each VI's description which balance series it supports, as
  `A&D EK_EW Zero.vi` and `A&D Internal Calibration.vi` already do.
- Document every VI, control, and indicator, including valid values and defaults.
- Preserve backwards compatibility: do not rename existing VIs, controls, or indicators,
  and do not change existing connector pane assignments.
- For new VIs, update `A&D VI Tree.vi` and the matching palette file (`dir.mnu`,
  `action_status.mnu`, `data.mnu`, `utility.mnu`, or `examples.mnu`).
- Update the copyright year on `A&D Initialize.vi`, `A&D VI Tree.vi`, and the examples.

# Testing

Summarize your results in the pull request: balance model and series, serial settings
used, and LabVIEW version.

- **Build:** Mass compile the `A&D/` folder. No broken VIs may be reported.
- **VI Analyzer:** Run VI Analyzer with the instrument driver configuration and resolve
  all failures.
- **Hardware:** Test new and modified VIs against a real A&D balance over RS-232,
  including both stable and unstable readings and series-specific VIs on the matching
  series.
- **Error handling:** Confirm serial timeouts and invalid responses produce a meaningful
  error, and that VIs do not run when an error is wired to error in (except Close).
- **Examples:** Run `A&D Example (Command).vi` and `A&D Example (Print Key).vi` end to end.
- **Palettes:** Confirm the palettes and `A&D VI Tree.vi` match and every VI appears.

# Developer Certificate of Origin (DCO)

   Developer's Certificate of Origin 1.1

   By making a contribution to this project, I certify that:

   (a) The contribution was created in whole or in part by me and I
       have the right to submit it under the open source license
       indicated in the file; or

   (b) The contribution is based upon previous work that, to the best
       of my knowledge, is covered under an appropriate open source
       license and I have the right under that license to submit that
       work with modifications, whether created in whole or in part
       by me, under the same open source license (unless I am
       permitted to submit under a different license), as indicated
       in the file; or

   (c) The contribution was provided directly to me by some other
       person who certified (a), (b) or (c) and I have not modified
       it.

   (d) I understand and agree that this project and the contribution
       are public and that a record of the contribution (including all
       personal information I submit with it, including my sign-off) is
       maintained indefinitely and may be redistributed consistent with
       this project or the open source license(s) involved.

(taken from [developercertificate.org](https://developercertificate.org/))

See [LICENSE](https://github.com/ASingh-NI/instr-driver-a-and-d-lv/blob/main/LICENSE.md) for details about how instr-driver-a-and-d-lv is
licensed.
