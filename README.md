# DOE HPC Resources for the Genesis Mission: ALCF, OLCF, NERSC

*Compiled 2026-10-20 for an MD + ML team.*

## How to read this

- We read the OLCF, NERSC and AmSC pages on 2026-10-20. Where a bullet has no link of its own, the link in its section heading is the source.
- `alcf.anl.gov`, `docs.alcf.anl.gov` and `anl.gov` block automated reads, so we read ALCF's facts from the source repository its docs site is built from, [argonne-lcf/user-guides](https://github.com/argonne-lcf/user-guides) (commit `0db16bd`, 2026-10-20). The ALCF links point to the published pages built from that source.
- "Not confirmed" means we found no official page that says it. Ask the facility before relying on it.
- GPU totals marked *(computed)* are nodes × GPUs per node. The facility doesn't state the total.

---

## At a glance

### Production GPU systems available now

Each cell links to its source. A "Not documented" cell has no link because the facility's docs don't mention that package for that system.

| System | Site | GPUs | Less than a node? | GROMACS | OpenMM | Containers | Compile & run your own code |
|---|---|---|---|---|---|---|---|
| **Aurora** | ALCF | [10,624 nodes × 6 Intel Max 1550 (128 GB) = 63,744](https://docs.alcf.anl.gov/aurora/) | [No (whole nodes)](https://docs.alcf.anl.gov/running-jobs/) | Not documented | Not documented | [Apptainer](https://docs.alcf.anl.gov/aurora/containers/containers/) | [Build](https://docs.alcf.anl.gov/aurora/compiling-and-linking/) (login nodes OK) · [Run](https://docs.alcf.anl.gov/aurora/running-jobs-aurora/) |
| **Polaris** | ALCF | [560 nodes × 4 A100 40 GB = 2,240](https://docs.alcf.anl.gov/polaris/) | [No (whole nodes)](https://docs.alcf.anl.gov/running-jobs/example-job-scripts/) | [Old prebuilt 2022.1 + recipe](https://docs.alcf.anl.gov/polaris/applications-and-libraries/applications/gromacs/) | [conda-forge (self-install)](https://docs.alcf.anl.gov/polaris/applications-and-libraries/applications/openmm/) | [Apptainer](https://docs.alcf.anl.gov/polaris/containers/containers/) | [Build](https://docs.alcf.anl.gov/polaris/compiling-and-linking/) (login nodes OK) · [Run](https://docs.alcf.anl.gov/polaris/running-jobs/) |
| **Sophia** | ALCF | [24 nodes × 8 A100 = 192](https://docs.alcf.anl.gov/sophia/) | [**Yes**: `by-gpu` queue (1, 2, 4, 8 GPUs)](https://docs.alcf.anl.gov/sophia/queueing-and-running-jobs/running-jobs/) | Not documented | Not documented | [Apptainer](https://docs.alcf.anl.gov/sophia/containers/containers/) | [Build](https://docs.alcf.anl.gov/sophia/compiling-and-linking/compiling-and-linking-overview/) (**compute nodes only**) · [Run](https://docs.alcf.anl.gov/sophia/queueing-and-running-jobs/running-jobs/) |
| **Frontier** | OLCF | [9,856 nodes × 4 MI250X (8 GCDs, 64 GB each) ≈ 78,848 GCDs](https://docs.olcf.ornl.gov/systems/frontier_user_guide.html) | [No (whole nodes, 8 GCDs)](https://docs.olcf.ornl.gov/systems/frontier_user_guide.html) | [No module](https://docs.olcf.ornl.gov/software/software_list/index.html) | [No module](https://docs.olcf.ornl.gov/software/software_list/index.html) | [Apptainer (+ Podman to build)](https://docs.olcf.ornl.gov/software/containers_on_frontier.html) | [Build](https://docs.olcf.ornl.gov/systems/frontier_user_guide.html#compiling) · [Run](https://docs.olcf.ornl.gov/systems/frontier_user_guide.html#running-jobs) |
| **Lux** | OLCF | [504 nodes × 8 MI355X (288 GB) = 4,032](https://docs.olcf.ornl.gov/systems/lux_user_guide.html) | [**Yes**: 1-GPU unit](https://docs.olcf.ornl.gov/systems/lux_user_guide.html) | Not confirmed | Not confirmed | [Apptainer](https://github.com/olcf/olcf_container_examples/tree/HEAD/lux/pytorch/amdrocmregistry) / [Kubernetes](https://docs.olcf.ornl.gov/systems/lux_user_guide.html) | [Build](https://docs.olcf.ornl.gov/systems/lux_user_guide.html#compiling) · [Run](https://docs.olcf.ornl.gov/systems/lux_user_guide.html#running-jobs) |
| **Perlmutter** | NERSC | [1,536 × 4 A100 40 GB + 256 × 4 A100 80 GB = 7,168](https://docs.nersc.gov/systems/perlmutter/architecture/) | [**Yes**: `shared` QOS (1 or 2 GPUs)](https://docs.nersc.gov/jobs/policy/) | [Container image](https://docs.nersc.gov/applications/gromacs/) ([module removed](https://docs.nersc.gov/systems/perlmutter/timeline/)) | Not documented | [Shifter](https://docs.nersc.gov/development/containers/shifter/how-to-use/), [podman-hpc](https://docs.nersc.gov/development/containers/podman-hpc/overview/) | [Clone & build walkthrough](https://docs.nersc.gov/tutorials/playbooks/compiling/) · [GPU builds](https://docs.nersc.gov/development/compilers/wrappers/) · [Run](https://docs.nersc.gov/systems/perlmutter/running-jobs/) |

In the last column, only NERSC's walkthrough starts from downloading or `git clone`-ing the source. On the other systems, clone the repository on a login node, then follow the Build page for compilers and modules. On Sophia, ALCF says not to compile on the login nodes, so build inside an interactive job.

### Announced, not yet available to users

| System | Site | Hardware | Expected |
|---|---|---|---|
| Equinox | ALCF | [10,000 NVIDIA Blackwell](https://www.energy.gov/articles/energy-department-announces-new-partnership-nvidia-and-oracle-build-largest-doe-ai) | ["2026"](https://www.energy.gov/articles/energy-department-announces-new-partnership-nvidia-and-oracle-build-largest-doe-ai) |
| Solstice | ALCF | [100,000 NVIDIA Blackwell](https://www.energy.gov/articles/energy-department-announces-new-partnership-nvidia-and-oracle-build-largest-doe-ai) | [No date given](https://www.energy.gov/articles/energy-department-announces-new-partnership-nvidia-and-oracle-build-largest-doe-ai) |
| Doudna | NERSC | [NVIDIA Vera Rubin](https://www.nersc.gov/what-we-do/resources/doudna-system) | [Delivery late 2026](https://www.nersc.gov/what-we-do/resources/doudna-system) |
| Discovery | OLCF | [AMD MI430X + EPYC Venice](https://www.olcf.ornl.gov/olcf-resources/compute-systems/discovery/) | [2028](https://www.olcf.ornl.gov/olcf-resources/compute-systems/discovery/) |

### Choosing a system for MD + ML

- For many small single-GPU MD jobs, use Perlmutter's `shared` QOS, Lux, or Sophia's `by-gpu` queue. All three charge only for the GPUs you use.
- On the whole-node systems, pack one task per GPU yourself. Each system's section below gives the facility's recipe.
- Polaris and Perlmutter provide the most MD software. Polaris has NAMD binaries and build recipes for GROMACS, AMBER and LAMMPS. Perlmutter has GROMACS, LAMMPS, NAMD and AMBER as NERSC container images.
- None of the three facilities documents an OpenMM module. Install it from conda-forge or pip on the NVIDIA systems, or use a container.
- On the AMD systems (Frontier, Lux), build MD codes for ROCm/HIP. On Aurora's Intel GPUs, build them with SYCL/oneAPI.
- CUDA/NGC images can't use the GPUs on Frontier, Lux or Aurora.

---

## 1. Genesis Mission access: AmSC and the Model Access Gateway

### American Science Cloud (AmSC)

- **What it is:** DOE's federated science cloud, which DOE calls "the cornerstone" of the Genesis Mission platform. ORNL runs it ([amsc.energy.gov](https://amsc.energy.gov/)).
- **Support:**
  - Contact form: <https://amsc.energy.gov/#support>
  - Support docs page: <https://docs.amsc.energy.gov/support/>
- **Getting started:** <https://docs.amsc.energy.gov/GM-getting-started>

### Model Access Gateway (MAG)

**What it provides** ([docs](https://docs.amsc.energy.gov/model-access-gateway)):
- LLMs, embedding models and MCP servers
- a chat interface and a basic agent builder
- agentic workflows and evaluations, listed as coming later

**Endpoints:**
- Dashboard: <https://mag.genesis.americansciencecloud.org/dashboard/>
- Chat: <https://chat.genesis.americansciencecloud.org>
- API: <https://mag.genesis.americansciencecloud.org>
- Projects: <https://my.amsc.energy.gov/dashboard>

**Models** ([model list](https://docs.amsc.energy.gov/model-selection), [providers](https://docs.amsc.energy.gov/model-names)):
- Claude, GPT, Gemini and embedding models.
- The docs list only commercial providers (OpenAI, Bedrock, Vertex, Azure). None of the listed models runs on DOE lab hardware.

**Rate limits:** 20 parallel requests and 120 requests per minute per user ([docs](https://docs.amsc.energy.gov/mag-rate-limits)).

**Who can use it:** Genesis RFA Phase I teams approved for MAG. The PI must first complete the Genesis Resources Planning Questionnaire ([FAQ](https://docs.amsc.energy.gov/faq)).

**Getting access** ([MAG get-started](https://docs.amsc.energy.gov/mag-get-started)):
1. Log in at my.amsc.energy.gov.
2. The PI approves your project membership.
3. Wait about 15 minutes.
4. The project requests a MAG allocation.
5. Create a Personal Access Token and use it as a bearer token.

### How Genesis teams get HPC time

- DOE program managers allocate compute in a separate step after awards are made. The RFA says "Computing and data storage resources will not be allocated at the time of funding awards" ([ASCR webinar slides](https://science.osti.gov/-/media/grants/pdf/foas-resources/2026/Genesis-Mission-RFA-Informational-Webinar-v2-public--clean--ASCR.pdf); [AmSC town-hall Q&A](https://amsc.energy.gov/wp-content/uploads/ORNL-Town-Hall-QA-04062026.pdf)).
- We found no Genesis-specific allocation call at any of the three facilities. Ask your DOE program manager, or write to GenesisMissionNOFO@science.doe.gov.
- The only dedicated Genesis share we found is on OLCF Lux. OLCF sets aside half of Lux's 3.5M node-hours per year for Genesis ([OLCF Lux](https://www.olcf.ornl.gov/olcf-resources/compute-systems/lux/)). The page doesn't say how to apply for that share, only to email support.
- You can also apply through the standard programs:

| Program | Covers | Status |
|---|---|---|
| [INCITE](https://doeleadershipcomputing.org/call-for-proposals/) | Aurora, Frontier | 2027 call closed 2026-06-15 |
| [ALCC](https://science.osti.gov/ascr/Facilities/Accessing-ASCR-Facilities/ALCC/Call-for-Proposals) | Frontier, Aurora, Polaris, Perlmutter | |
| ALCF Director's Discretionary | ALCF systems | Rolling ([link](https://www.alcf.anl.gov/science/directors-discretionary-allocation-program)) |
| OLCF Director's Discretion | OLCF systems | Rolling ([link](https://my.olcf.ornl.gov/project-application-new)) |
| NERSC ERCAP | Perlmutter | AY2027 closed 2026-10-05; NERSC accepts proposals year-round while time remains ([call](https://www.nersc.gov/users/user-news/call-for-proposals-for-nersc-ay-2027)) |

---

## 2. ALCF: Argonne Leadership Computing Facility

- **Support:** support@alcf.anl.gov ([ticket docs](https://docs.alcf.anl.gov/support/ticket/)) and the [ALCF Users Slack](https://docs.alcf.anl.gov/support/get-help/alcf-users-slack/).
- **Systems in the docs:** Aurora, Polaris, Sophia, Crux (CPU only) and the AI Testbed ([machines](https://docs.alcf.anl.gov/machines/)).
- **Scheduler:** PBS Pro on all of them.
- **Charging:** node-hours ([allocation management](https://docs.alcf.anl.gov/account-project-management/allocation-management/allocation-management/)). The exact formula is not documented.

### 2.1 Aurora (Intel exascale)

**Scale** ([Aurora](https://docs.alcf.anl.gov/aurora/))
- **Nodes:** 10,624.
- **CPU:** 2× Xeon Max 9470C per node (52 cores each).
- **GPU:** 6× Intel Data Center GPU Max 1550 (Ponte Vecchio) per node, 128 GB HBM2e each. Each GPU has 2 tiles, so a node has 12 tiles.
- **Total:** 63,744 GPUs.
- **Recent update:** ALCF updated the software stack on 2026-09-28 (oneAPI 2026.1, SLES 15 SP7). Code built before then must be recompiled ([system updates](https://docs.alcf.anl.gov/aurora/system-updates/)).

**Scheduling** ([running jobs](https://docs.alcf.anl.gov/aurora/running-jobs-aurora/))

| Queue | Nodes | Max walltime |
|---|---|---|
| debug | 1–2 | 1 h |
| debug-scaling | 2–256 | 1 h |
| prod | 256+ | 12–24 h by size |
| capacity | 1–16 | 168 h |

- **Less than a node:** no. ALCF allocates whole nodes ([PBS overview](https://docs.alcf.anl.gov/running-jobs/)).
- **Packing tasks onto a node** (same running-jobs page):
  - Launch several `mpiexec ... &` commands, each with its own `ZE_AFFINITY_MASK=<gpu>.<tile>` and `--cpu-bind=list:`, then `wait`. That gives up to 12 single-tile tasks per node.
  - Or use the wrapper scripts `gpu_tile_compact.sh` / `gpu_dev_compact.sh`, or `--gpu-bind=list:0.0:0.1:...`.
  - `ZEX_NUMBER_OF_CCS` allows up to 48 processes per node, similar to MPS.
- **Ensemble and job-array examples:** <https://docs.alcf.anl.gov/running-jobs/example-job-scripts/>

**Preinstalled software**

| Package | Status | Source |
|---|---|---|
| PyTorch | `module load frameworks` (2026.1.0: PyTorch 2.13, vLLM) | [frameworks](https://docs.alcf.anl.gov/aurora/data-science/frameworks/) |
| TensorFlow | **Removed** as of frameworks/2026.1.0 | [TensorFlow](https://docs.alcf.anl.gov/aurora/data-science/frameworks/tensorflow/) |
| JAX | Dropped in the 2025-09 release; not since restored | [system updates](https://docs.alcf.anl.gov/aurora/system-updates/) |
| LAMMPS | Build-it-yourself recipes (Kokkos-SYCL); binaries on request | [LAMMPS](https://docs.alcf.anl.gov/aurora/applications-and-libraries/applications/lammps/) |
| GROMACS, OpenMM, NAMD, AMBER | **No Aurora page; not confirmed.** Ask support. | — |

**Containers** ([Aurora containers](https://docs.alcf.anl.gov/aurora/containers/containers/))
- **Runtime:** Apptainer (`module load apptainer`). Docker images are converted to Apptainer images.
- **Build on a compute node, through the proxy:**
  ```bash
  qsub -I -q debug -l select=1,walltime=60:00 -A <project> -l filesystems=<fs>
  export HTTP_PROXY=http://proxy.alcf.anl.gov:3128 HTTPS_PROXY=http://proxy.alcf.anl.gov:3128
  export http_proxy=$HTTP_PROXY https_proxy=$HTTPS_PROXY
  module load apptainer
  apptainer build --fakeroot myimage.sif docker://<image>
  ```
- **GPU stack:** build images on Intel's GPU stack; ALCF's example starts from `intel/oneapi-hpckit`. CUDA/NGC images can't use Aurora's GPUs.

**Custom software without containers**
- **Python:** `python3 -m venv --system-site-packages` on top of `frameworks`, or conda ([Python](https://docs.alcf.anl.gov/aurora/data-science/python/)). At more than about 1000 nodes, use Copper for imports (same page).
- **Spack:** your own Spack with ALCF's configs in `/opt/aurora/<PE>/spack/.../config` ([Spack PE](https://docs.alcf.anl.gov/aurora/applications-and-libraries/libraries/spack-pe/)).
- **Extra modules:** `module use /soft/modulefiles` ([getting started](https://docs.alcf.anl.gov/aurora/getting-started-on-aurora/)).

### 2.2 Polaris (NVIDIA A100)

**Scale** ([Polaris](https://docs.alcf.anl.gov/polaris/))
- **Nodes:** 560.
- **CPU:** 1× EPYC 7543P per node (32 cores), 512 GB.
- **GPU:** 4× A100 SXM 40 GB per node, NVLink.
- **Total:** 2,240 GPUs.
- **Recent update:** in August 2026 Polaris moved to the CUDA 13 driver and PE 26.03 ([system updates](https://docs.alcf.anl.gov/polaris/system-updates/)).

**Scheduling** ([running jobs](https://docs.alcf.anl.gov/polaris/running-jobs/))

| Queue | Nodes | Max walltime |
|---|---|---|
| debug | 1–2 | 1 h |
| debug-scaling | 1–10 | 1 h |
| prod | 10–496 | 3–24 h by size |
| preemptable | 1–10 | 72 h |
| capacity | 1–4 | 168 h |

- **Less than a node:** no. "Jobs on Polaris cannot share nodes with other jobs" ([example scripts](https://docs.alcf.anl.gov/running-jobs/example-job-scripts/)).
- **Packing tasks onto a node** ([using GPUs](https://docs.alcf.anl.gov/polaris/running-jobs/using-gpus/)):
  - Run 4 backgrounded launches, each pinned to one GPU with `CUDA_VISIBLE_DEVICES` and NUMA-matched to its CPU cores:
    ```bash
    export CUDA_VISIBLE_DEVICES=0; mpiexec -n 8 --ppn 8 --cpu-bind list:24:25:26:27:28:29:30:31 ./app &
    export CUDA_VISIBLE_DEVICES=1; mpiexec -n 8 --ppn 8 --cpu-bind list:16:17:18:19:20:21:22:23 ./app &
    export CUDA_VISIBLE_DEVICES=2; mpiexec -n 8 --ppn 8 --cpu-bind list:8:9:10:11:12:13:14:15 ./app &
    export CUDA_VISIBLE_DEVICES=3; mpiexec -n 8 --ppn 8 --cpu-bind list:0:1:2:3:4:5:6:7 ./app &
    wait
    ```
  - ALCF supports NVIDIA MPS through `enable_mps_polaris.sh`. We think it is the best way to run several small MD systems on one GPU; ALCF doesn't say so.
  - MIG is disabled.

**Preinstalled software**

| Package | Status | Source |
|---|---|---|
| PyTorch, TensorFlow, JAX | `module use /soft/modulefiles; module load conda; conda activate base`. `conda/2026-10-01` (PyTorch 2.14, TF 2.21, JAX 0.11.1, CUDA 13) becomes the default in a few weeks, and venvs built on the old module will then need rebuilding. | [Python](https://docs.alcf.anl.gov/polaris/data-science/python/), [updates](https://docs.alcf.anl.gov/polaris/system-updates/) |
| GROMACS | Prebuilt 2022.1 at `/soft/applications/Gromacs/gromacs-2022.1`, plus a build recipe. **Likely stale** (built for CUDA 11, before the CUDA 13 upgrade). | [GROMACS](https://docs.alcf.anl.gov/polaris/applications-and-libraries/applications/gromacs/) |
| NAMD | Prebuilt `namd3` in `/soft/applications/namd`; recommended | [NAMD](https://docs.alcf.anl.gov/polaris/applications-and-libraries/applications/namd/) |
| AMBER | Build recipe (Amber24); no binary | [AMBER](https://docs.alcf.anl.gov/polaris/applications-and-libraries/applications/amber/) |
| LAMMPS | Build recipe; binaries on request | [LAMMPS](https://docs.alcf.anl.gov/polaris/applications-and-libraries/applications/lammps/) |
| OpenMM | `conda install -c conda-forge openmm` into your own env. **Page is stale** (references conda/2022-07-19 and CUDA 11.4). | [OpenMM](https://docs.alcf.anl.gov/polaris/applications-and-libraries/applications/openmm/) |

**Containers** ([Polaris containers](https://docs.alcf.anl.gov/polaris/containers/containers/))
- **Runtime:** Apptainer 1.4.1. Build and run on compute nodes only.
- **Building:**
  ```bash
  qsub -I -A <project> -q debug -l select=1 -l walltime=01:00:00 \
       -l filesystems=home:eagle -l singularity_fakeroot=true
  ml use /soft/modulefiles; ml spack-pe-base; ml apptainer
  export APPTAINER_TMPDIR=/local/scratch/apptainer-tmpdir APPTAINER_CACHEDIR=/local/scratch/apptainer-cachedir
  export HTTP_PROXY=http://proxy.alcf.anl.gov:3128 HTTPS_PROXY=http://proxy.alcf.anl.gov:3128
  export http_proxy=$HTTP_PROXY https_proxy=$HTTPS_PROXY
  apptainer build --fakeroot myimage.sif docker://nvcr.io/nvidia/pytorch:<tag>
  ```
- **Image sources:** NGC and Docker Hub both work. ALCF's own images are at [argonne-lcf/container-registry](https://github.com/argonne-lcf/container-registry). Choose a CUDA 13-compatible tag; the docs' `22.06` example is old.
- **MPI in containers:** load `cray-mpich-abi` and bind `/opt` and `/var/run/palsd`.

**Custom software without containers**
- **Python:** a venv on the conda module with `--system-site-packages` ([Python](https://docs.alcf.anl.gov/polaris/data-science/python/)).
- **Builds:** PrgEnv-nvidia or PrgEnv-gnu with `cudatoolkit-standalone`.
- **Spack:** `spack-pe-base` and `spack-pe-gnu` modules ([Spack PE](https://docs.alcf.anl.gov/polaris/applications-and-libraries/libraries/spack-pe/)).

### 2.3 Sophia (NVIDIA DGX A100)

**Scale** ([Sophia](https://docs.alcf.anl.gov/sophia/))
- **Nodes:** 24 DGX A100.
- **GPU:** 8× A100 per node (22 nodes with 40 GB GPUs, 2 with 80 GB).
- **Total:** 192 GPUs.

**Scheduling** ([running jobs](https://docs.alcf.anl.gov/sophia/queueing-and-running-jobs/running-jobs/))
- **Less than a node:** yes. Sophia is the only ALCF GPU system that allows it.
  - The `by-gpu` queue (the default) takes `-l select=N` with N = 1, 2, 4 or 8 GPUs, up to 24 h.
  - `by-node` covers 1–8 nodes, 24 h.
- **Limits:** 5 running and 20 queued jobs per project.
- **Charging for by-gpu jobs:** not confirmed.

**Software**
- **Python / ML:** the same `conda` module as Polaris (PyTorch, TF, JAX) ([Python](https://docs.alcf.anl.gov/sophia/data-science/python/)).
- **MD packages:** none documented.

**Containers:** Apptainer 1.3.3 on compute nodes, using the same `docker://` build pattern ([Sophia containers](https://docs.alcf.anl.gov/sophia/containers/containers/)).

### 2.4 Other ALCF resources

- **Crux:** 256 CPU-only nodes ([Crux](https://docs.alcf.anl.gov/crux/)).
- **AI Testbed:** Cerebras CS-3, Graphcore, Groq, and SambaNova SN40L (inference only, through the ALCF Inference Service) ([AI Testbed](https://docs.alcf.anl.gov/ai-testbed/)). ALCF documents no MD software on any of them.
- **Equinox and Solstice:** not in the user docs yet, and we couldn't confirm their status. ALCF's [Genesis page](https://www.alcf.anl.gov/genesis-mission) blocks automated reads, so check it in a browser.

---

## 3. OLCF: Oak Ridge Leadership Computing Facility

- **Support:** help@olcf.ornl.gov or the [ticket form](https://www.olcf.ornl.gov/for-users/getting-started/submit-ticket/) ([support](https://docs.olcf.ornl.gov/support/index.html)).
- **Allocations are per system.** Frontier, Lux and the analysis clusters each have their own ([projects](https://docs.olcf.ornl.gov/accounts/accounts_and_projects.html)).
- **Scheduler:** Slurm.
- **Retired and retiring systems:**
  - Summit was retired on 2024-11-15 ([Summit](https://docs.olcf.ornl.gov/systems/summit_user_guide.html)).
  - **Andes will be decommissioned on 2026-11-02** ([Andes](https://docs.olcf.ornl.gov/systems/andes_user_guide.html)). Its replacement is Riker, a small analysis cluster with 16 L40S GPUs ([Riker](https://docs.olcf.ornl.gov/systems/riker_user_guide.html)).

### 3.1 Frontier (AMD MI250X)

**Scale** ([Frontier user guide](https://docs.olcf.ornl.gov/systems/frontier_user_guide.html), "FUG" below)
- **Nodes:** 9,856.
- **CPU:** 1× 64-core EPYC per node, 512 GB. 56 cores are usable.
- **GPU:** 4× MI250X per node. Each MI250X has 2 GCDs, so a node has 8 GCDs of 64 GB each. Slurm treats each GCD as one GPU.
- **Total:** about 78,848 GCDs *(computed)*.

**Scheduling** (FUG, "Scheduling Policy")
- **Less than a node:** no. The charge is nodes × elapsed time. One node (8 GCDs) is the minimum.
- **Walltime depends on job size** in the `batch` partition:

| Nodes | Max walltime |
|---|---|
| 1–91 | 2 h |
| 92–183 | 6 h |
| 184+ | 12 h |

- **Longer runs for small jobs:** the `extended` partition allows 24 h on up to 64 nodes, with 1 running job per user.
- **Other queues:** `-q debug` (2 h, 1 job per user).
- **Packing single-GCD tasks** (FUG, "Multiple Independent Job Steps" and "Ensemble Jobs"):
  ```bash
  for i in {1..8}; do
    srun -u -N1 -n1 -c1 --gpus-per-task=1 --gpu-bind=closest ./task.sh $i &
    sleep 1
  done
  wait
  ```
  - At scale, OLCF recommends one `srun` with a wrapper script: `srun -N $SLURM_NNODES -n $((SLURM_NNODES*8)) -c 7 --gpus-per-task=1 --gpu-bind=closest ./wrapper.sh`.
  - Avoid running more than about 100 concurrent `srun` steps.
  - Flux is available for larger ensembles.
  - Always pass a GPU option. Otherwise every task sees all 8 GCDs (known issue OLCFDEV-1061).

**Preinstalled software** ([software catalog](https://docs.olcf.ornl.gov/software/software_list/index.html))

| Package | Status | Source |
|---|---|---|
| LAMMPS | Module, e.g. `lammps/20250722.3-gpu-mpi-omp` (after loading cpe/26.03, PrgEnv-gnu, rocm/7.0.2, cray-mpich) | catalog |
| PLUMED | Module (`plumed/2.10.0-mpi`) | catalog |
| GROMACS, OpenMM, AMBER, NAMD | No module. Build them yourself or use a container. | catalog |
| PyTorch | Self-install: ROCm wheels in a conda env (torch 2.10 / ROCm 7.1) | [PyTorch on Frontier](https://docs.olcf.ornl.gov/software/analytics/pytorch_frontier.html) |
| JAX | Self-install: `jax-rocm7-plugin` 0.7.1 | [JAX](https://docs.olcf.ornl.gov/software/analytics/jax.html) |
| TensorFlow | AMD's `rocm/tensorflow` container only | [containers](https://docs.olcf.ornl.gov/software/containers_on_frontier.html) |
| Python | `module load miniforge3/23.11.0-0`. Do not run `conda init`. Put environments in `/ccs/proj/<proj>/`. | [Python](https://docs.olcf.ornl.gov/software/python/index.html) |

**PyTorch install recipe** (from the PyTorch on Frontier page):
```bash
module load PrgEnv-gnu/8.7.0 cpe/26.03 miniforge3/23.11.0-0 rocm/7.1.1 craype-accel-amd-gfx90a
export LD_LIBRARY_PATH=$CRAY_LD_LIBRARY_PATH:$LD_LIBRARY_PATH
conda create -p /ccs/proj/<proj>/envs/torch python=3.12 -c conda-forge
conda activate /ccs/proj/<proj>/envs/torch
pip install torch==2.10.0 torchvision==0.25.0 torchaudio==2.10.0 --index-url https://download.pytorch.org/whl/rocm7.1
```
For OpenMM, build it from source against ROCm/HIP. OLCF documents no route.

**Containers** ([Containers on Frontier](https://docs.olcf.ornl.gov/software/containers_on_frontier.html))
- **Runtime:** Apptainer 1.3.6 for building and running.
- **Getting a Docker image onto Frontier:**
  - Pull directly: `apptainer pull myimage.sif docker://<image>`.
  - Or build from a Dockerfile with Podman, then convert. This needs subuid/subgid mappings, requested from help@olcf.ornl.gov:
    ```bash
    podman build --network host -t myimg .
    podman save -o myimg.tar myimg
    apptainer build myimg.sif docker-archive://myimg.tar
    ```
    Podman cannot *run* containers on Frontier.
- **MPI:** the image needs MPICH 3.4.2, ABI-compatible with the host. The host `cray-mpich-abi` is bind-mounted in at run time. Helper modules: `module load olcf-container-tools` then `apptainer-enable-mpi` and `apptainer-enable-gpu`.
- **Official base images:** `docker://savannah.ornl.gov/olcf-container-images/cpe:<tag>`.
- **AMD's ML images:** `rocm/pytorch`, `rocm/tensorflow`, `rocm/jax-community`.
- **Examples:** [olcf/olcf_container_examples](https://github.com/olcf/olcf_container_examples). It includes LAMMPS but not GROMACS or OpenMM.

**Custom software without containers**
- **Compilers:** the Cray PE (CCE, AMD and GCC) plus ROCm modules. The recommended pairings are cpe/25.09 + rocm/6.4.2 and cpe/26.03 + rocm/7.x (FUG). With a non-default CPE, `export LD_LIBRARY_PATH=$CRAY_LD_LIBRARY_PATH:$LD_LIBRARY_PATH`.
- **User-Managed Software:** `module load ums`, then project modules such as E4S (`ums002`) ([UMS](https://docs.olcf.ornl.gov/software/UMS/index.html)).
- **Spack:** the [Spack environments page](https://docs.olcf.ornl.gov/software/spack_environments.html) is out of date: it targets Summit, and its template repo is archived. Use OLCF modules as Spack externals.

### 3.2 Lux (AMD MI355X AI cluster)

**Scale** ([Lux user guide](https://docs.olcf.ornl.gov/systems/lux_user_guide.html))
- **Nodes:** 504 HPE XD685.
- **CPU:** 2× 64-core EPYC 9575F per node, 3 TB RAM.
- **GPU:** 8× AMD MI355X per node, 288 GB HBM3E each.
- **Total:** 4,032 GPUs.
- **Access modes:** a Slurm side and a Kubernetes side.
- **Status:** the user guide documents Lux as in production. The [facility page](https://www.olcf.ornl.gov/olcf-resources/compute-systems/lux/) still says it "will be deployed within the next six months"; that page is out of date.

**Scheduling** (user guide)
- **Less than a node:** yes.
  - The unit is 1 GPU, which comes with 16 cores and 375 GB RAM.
  - `--exclusive` gives a whole node.
- **Charging:** 0.125 node-hours per GPU-hour.
- **Walltime:** up to 48 h, on 1–484 nodes.
- **Packing:** same `srun --gpus-per-task=1 --gpu-bind=closest ... &` pattern as Frontier.
- **MPI and RCCL:** our first read of the guide found MPI described as "not yet officially verified", with a 16-node limit for MPI jobs and RCCL over the AMD Pollara NICs as the main communication path. We couldn't find those sentences again on a second read, so check the guide before relying on them.
- **Kubernetes:** pods of up to 8 GPUs and 48 h, in the `<proj>-gpu` namespace.
- **Genesis share:** half of Lux's 3.5M node-hours per year ([facility page](https://www.olcf.ornl.gov/olcf-resources/compute-systems/lux/)).

**Software**
- **Modules:** `rocm/7.2.4` and `rocm/7.14.0`, `openmpi`, `mpich`, `amdfftw`.
- **Not confirmed:** MD packages, conda and PyTorch guidance.

**Containers**
- **Kubernetes side:** pods run ordinary Docker/OCI images directly.
- **Slurm side:** the user guide doesn't describe Apptainer. OLCF's example repo builds `docker://docker.io/rocm/pytorch:rocm7.14.1_...` with Apptainer, and notes ROCm 7.14 is needed for the RCCL network plugin ([example](https://github.com/olcf/olcf_container_examples/tree/HEAD/lux/pytorch/amdrocmregistry)).

---

## 4. NERSC: National Energy Research Scientific Computing Center

- **Support:** [NERSC Help Portal](https://help.nersc.gov/) ([getting help](https://docs.nersc.gov/getting-started/)).
- **Scheduler:** Slurm.

### 4.1 Perlmutter (NVIDIA A100)

**Scale** ([architecture](https://docs.nersc.gov/systems/perlmutter/architecture/))

| Partition | Nodes | Per node |
|---|---|---|
| GPU 40 GB | 1,536 | 1× EPYC 7763, 4× A100 40 GB |
| GPU 80 GB | 256 | 1× EPYC 7763, 4× A100 80 GB |
| CPU | 3,072 | 2× EPYC 7763, no GPU |

- **Total:** 7,168 GPUs *(computed)*.
- **Selecting the 80 GB nodes:** `-C "gpu&hbm80g"`.
- **Requesting GPUs:** request them explicitly with one of the `--gpus*` options ([running jobs](https://docs.nersc.gov/systems/perlmutter/running-jobs/)).

**Scheduling** ([queue policy](https://docs.nersc.gov/jobs/policy/))

| QOS | Max nodes | Max walltime | Notes |
|---|---|---|---|
| regular | — | 48 h | Exclusive nodes |
| shared | 0.5 node | 48 h | 1 or 2 GPUs, charged by fraction of the node |
| debug | 8 | 30 min | |
| interactive | 4 | 4 h | `salloc` only |
| preempt | 128 | 48 h | Charge drops to 0.25 after 2 h; can be preempted |
| premium | — | 48 h | 2× charge |

- **Less than a node:** yes.
  - "GPU jobs in the shared QOS may request 1 or 2 GPUs and will be allocated a corresponding 16 CPU cores and 64 GB RAM or 32 CPU cores and 128 GB RAM."
  - Example charge: 10 h on 2 GPUs = 5 node-hours.
  - A job that needs 3 or 4 GPUs has to request a full node.
- **Packing single-GPU tasks into one node** ([running jobs](https://docs.nersc.gov/systems/perlmutter/running-jobs/), "Single-GPU tasks in parallel"):
  ```bash
  #SBATCH -C gpu
  #SBATCH -N 1
  #SBATCH --ntasks-per-node=4
  for i in 0 1 2 3; do
    srun --exact -u -n 1 --gpus-per-task 1 -c 32 --mem-per-gpu=55G ./task.sh $i &
  done
  wait
  ```
  - The same page shows how to use CUDA MPS to run more than one process per GPU.
  - For hundreds of tasks, use [GNU Parallel](https://docs.nersc.gov/jobs/workflow/gnuparallel/) rather than many `srun` calls or job arrays.

**Preinstalled software**

NERSC provides its supported MD codes as Shifter container images. It removed the GROMACS modules in January 2025 ([timeline](https://docs.nersc.gov/systems/perlmutter/timeline/)).

| Package | How provided | Source |
|---|---|---|
| GROMACS | `docker:nersc/gromacs:23.2` (also `_plumed`, `_colvars` variants). PME runs on the CPU in these images. | [GROMACS](https://docs.nersc.gov/applications/gromacs/) |
| LAMMPS | `nersc/lammps_all:23.08` and related images, plus a Kokkos build recipe | [LAMMPS](https://docs.nersc.gov/applications/lammps/) |
| NAMD | `nvcr.io/hpc/namd:3.0-beta5` (GPU, single-node) | [NAMD](https://docs.nersc.gov/applications/namd/) |
| AMBER | `docker:nersc/amber_gpu:22` | [AMBER](https://docs.nersc.gov/applications/amber/) |
| OpenMM | Not documented. Install it yourself with conda or pip, or use a container. | — |
| PyTorch | `module load pytorch/<ver>` (2.13.0 newest); NGC-based `nersc/pytorch` images | [PyTorch](https://docs.nersc.gov/machinelearning/pytorch/) |
| TensorFlow | `module load tensorflow/<ver>` | [TensorFlow](https://docs.nersc.gov/machinelearning/tensorflow/) |
| JAX | Not documented. Install it yourself. | — |
| Python | `module load python` or `module load conda` (Miniforge) | [NERSC Python](https://docs.nersc.gov/development/languages/python/nersc-python/) |

**GROMACS run example** (from the GROMACS page):
```bash
#SBATCH --image docker:nersc/gromacs:23.2
srun --cpu-bind=cores --gpu-bind=none --module cuda-mpich shifter gmx_mpi mdrun -nb gpu -bonded gpu ...
```

**Containers** ([overview](https://docs.nersc.gov/development/containers/))
NERSC runs two container runtimes. It recommends podman-hpc for new users, and still runs its own MD images under Shifter.

- **podman-hpc** ([docs](https://docs.nersc.gov/development/containers/podman-hpc/overview/)):
  - Pull with `podman-hpc pull <image>`.
  - You can build a Dockerfile on Perlmutter itself with `podman-hpc build -t name:tag .`, then `podman-hpc migrate name:tag` so jobs can use the image.
  - Run with flags: `srun podman-hpc run --rm --gpu [--mpi|--cuda-mpi|--nccl-cu12] <image> <cmd>`.
  - Apptainer/Singularity image formats are supported.
- **Shifter** ([docs](https://docs.nersc.gov/development/containers/shifter/how-to-use/)):
  - Pull with `shifterimg -v pull docker:<image>:<tag>` (use `shifterimg login` for private images).
  - In jobs: `#SBATCH --image=docker:...`, then `srun shifter <cmd>`.
  - Modules: `--module=gpu`, `cuda-mpich` (CUDA-aware MPI), and `nccl-plugin` (NCCL over Slingshot).
- **registry.nersc.gov** ([registry](https://docs.nersc.gov/development/containers/registry/)):
  - A private project registry. Request access by ticket.
  - It also caches pulls from docker.io, ghcr.io, nvcr.io (NGC), quay.io and others.
  - NGC images can use Perlmutter's GPUs.

**Custom software without containers**
- **conda / venv:** install with `conda create --prefix /global/common/software/<proj>/myenv`. NERSC recommends that location because imports from it are fast at scale. Compute nodes mount it read-only, so install from a login node ([NERSC Python](https://docs.nersc.gov/development/languages/python/nersc-python/), [global common](https://docs.nersc.gov/filesystems/global-common/)).
- **Spack:** `module load spack` comes preconfigured for the NERSC PE ([Spack](https://docs.nersc.gov/development/build-tools/spack/)).
- **E4S:** provided as Shifter images only ([E4S](https://docs.nersc.gov/applications/e4s/)).
- **Cray PE:** `cc`/`CC`/`ftn` with `cudatoolkit` and `craype-accel-nvidia80` ([compiler wrappers](https://docs.nersc.gov/development/compilers/wrappers/)).
- **Sharing builds with the team:** install under `/global/common/software/<proj>/` and share modulefiles there ([installing and sharing](https://docs.nersc.gov/development/installing-sharing-software/)).

### 4.2 Doudna (NERSC-10), not yet available

- **Delivery:** "scheduled to be delivered in late 2026" ([Doudna](https://www.nersc.gov/what-we-do/resources/doudna-system)).
- **Announced hardware:**
  - Dell systems on the NVIDIA Vera Rubin platform, with Quantum-X800 InfiniBand.
  - NERSC says at least 10× Perlmutter's performance, and says containers will be central to its user environment.
  - NERSC hasn't published node or GPU counts.
- **User docs:** none yet. The AY2027 allocation call offers Perlmutter only ([call](https://www.nersc.gov/users/user-news/call-for-proposals-for-nersc-ay-2027)).
- **Early-access system:** Cech (72 Grace CPUs + 144 Blackwell GPUs) is staff-only for now and "will be used to support the Genesis Mission" ([NERSC news](https://www.nersc.gov/news-and-events/news/berkeley-lab-takes-major-step-toward-doudna-with-delivery-of-early-access-system-cech)).

---

## 5. Known documentation problems

The facility pages below are out of date or contradict each other. Check them with the facility before relying on them.

- **ALCF Polaris GROMACS:** the prebuilt binary and recipe target CUDA 11 and predate the CUDA 13 upgrade.
- **ALCF Polaris OpenMM:** the page is stale and references a 2022 conda module.
- **ALCF Aurora getting-started page:** it still lists TensorFlow in `frameworks`, which was removed.
- **ALCF container examples:** they use 2022 NGC tags.
- **OLCF Lux facility page:** it says the system is not yet deployed, but the user guide shows it in production.
- **OLCF Spack environments page:** it targets Summit.
- **OLCF Summit:** it still appears on the compute-systems index, though it is retired.
- **NERSC systems index:** <https://docs.nersc.gov/systems/> gives 1,536 GPU nodes, leaving out the 256 nodes with 80 GB GPUs.
- **NERSC MD images:** they are from 2023–24 (GROMACS 23.2, LAMMPS 23.08, NAMD 3.0b5).
- **Equinox:** DOE's October 2025 announcement said "expected to be delivered in 2026". A [GitHub issue on argonne-lcf/user-guides](https://github.com/argonne-lcf/user-guides/issues/1329) quotes anl.gov as now saying "in the planning stages". We couldn't open the anl.gov page to check.

## 6. Questions to send the facilities

1. **ALCF:** Is GROMACS or OpenMM available or planned for Aurora? Does the Polaris GROMACS 2022.1 binary still run after the CUDA 13 upgrade? How are Sophia `by-gpu` jobs charged? What is the Equinox access route for Genesis teams?
2. **OLCF:** How do Genesis teams apply for the Genesis half of Lux? Which MD packages and container workflows are supported on Lux's Slurm side?
3. **NERSC:** Is there a Genesis allocation route on Perlmutter or Doudna? When do Doudna user accounts open?
4. **AmSC / DOE program manager:** What is the process for compute allocations for awarded Genesis projects?
