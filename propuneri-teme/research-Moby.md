# Research Projects

Below, you can find research project topics split into several categories. If you are
interested in a topic, please contact the coordinator (the first name in parentheses)
for further information. Here is the contact info:
- RaduC → Radu-Ioan Ciobanu, radu.ciobanu@upb.ro
- RaduM → Radu Marin, radu.marin@upb.ro
- AlexC → Alexandru Costan, alexandru.costan@upb.ro
- AlexT → George-Alexandru Tudor, george.tudor1906@upb.ro
- Alexandra → Alexandra Ion, alexandra_ana.ion@upb.ro

---

## **Decentralized, Opportunistic, and Personalized Federated Learning**

Decentralized and opportunistic federated learning investigates how mobile and edge
devices can collaboratively train or personalize machine-learning models without
relying continuously on a central coordinator. Unlike conventional federated
learning, communication opportunities may be intermittent, short-lived, and
determined by human mobility, while participating devices may differ significantly in
data, resources, connectivity, and model architecture. Research in this area focuses
on partner selection, temporal communication graphs, asynchronous learning,
personalized models, delay-tolerant exchange, and the relationship between mobility
patterns and learning performance.

- **T1. Contact-Aware Partner Selection for Opportunistic Federated Learning:**
  Research and develop mechanisms that allow a mobile device to decide whether
  collaboration with an encountered peer is beneficial, considering model similarity,
  data complementarity, expected contact duration, battery level, and communication
  cost. **Type:** Research. (RaduC, AlexT)
- **T2. Federated Learning over Temporal aaund Opportunistic Contact Graphs:**
  Research how convergence, personalization, fairness, and information propagation are
  affected when the communication graph evolves according to human mobility rather
  than following a fixed network topology. **Type:** Research. (RaduC, AlexT)
- **T3. Opportunistic Knowledge Distillation between Heterogeneous Devices:**
  Research and develop serverless learning mechanisms through which devices running
  different model architectures exchange predictions, prototypes, embeddings, prompts,
  or other compact knowledge representations during short encounters. **Type:**
  Research + Applied. (RaduC, AlexT)
- **T4. Community-Aware Personalized Federated Learning:** Research methods that
  identify groups of devices with compatible data or mobility patterns and
  dynamically construct specialized models for each community without requiring
  predefined clusters. **Type:** Research. (RaduC, AlexT)
- **T5. Store-Carry-Learn: Delay-Tolerant Model Exchange in Mobile Networks:** Research
  and develop mechanisms that store, transport, prioritize, and progressively exchange
  model updates across intermittent contacts, studying the impact of staleness, partial
  transfers, replication, and update expiration. **Type:** Research + Applied. (RaduC,
  AlexT)
- **T6. Experimental Framework for Opportunistic Federated Learning:** Research,
  design, and implement a reproducible framework that evaluates decentralized learning
  using real mobility traces, MobEmu, ONE or ns-3 simulations, and a small Android or
  Raspberry Pi testbed. **Type:** Research + Applied. (RaduC, AlexC, AlexT)
- **T7. Evaluating Personalized Federated Learning across Diverse Clients and
  Infrastructures:** A model trained collaboratively may work well for some
  participants but less well for others, especially when their data or devices are very
  different. Compare existing personalization approaches on clients with different data
  distributions, computing resources, and network connections. Measure both prediction
  quality for each client and system costs such as training time and communication. The
  focus is on realistic evaluation and trade-offs, rather than on discovering new mobile
  communities or peer-to-peer contacts. **Type:** Research + Applied. (AlexC, RaduC)
- **T8. Device-to-Device Communication for Collaborative Learning:** Research and
  develop ways for nearby smartphones to exchange model updates directly, using
  technologies such as Bluetooth or Wi-Fi Direct, measuring how distance, encounter
  duration, and update size affect whether an exchange succeeds. **Type:** Research +
  Applied. (RaduM, RaduC)
- **T9. Encounter Detection and Contact-Duration Prediction on Smartphones:** Research
  and develop an Android application that detects nearby phones with BLE, records real
  encounters between volunteers, and predicts how long a contact will last from signal
  strength, time of day, and previous meetings, so that a device knows in advance how
  much model data it can exchange. **Type:** Research + Applied. (AlexT, RaduC)
- **T10. Merging Models Learned on Different Phones without Forgetting:** When two
  phones exchange models trained on different local data, simple averaging can erase
  what each of them learned. Research and compare model-merging methods, such as
  weighted averaging, task arithmetic, or TIES merging, for pairwise exchanges,
  measuring accuracy on the device’s own data and on the peer’s data after repeated
  encounters. **Type:** Research. (AlexT, RaduC)
- **T11. Serverless Collaborative Object Detection:** Research and develop an Android
  application in which phones learn to recognize landmarks, such as campus buildings,
  and improve their detectors by exchanging model updates directly when they meet, then
  compare the result with server-based federated training on the same devices.
  **Type:** Research + Applied. (AlexT, RaduC)
- **T12. Event-Based Photo Sharing and On-Device Organization over Local Wi-Fi:**
  Research and develop an Android application through which phones at the same event
  exchange photos directly over the local Wi-Fi network, without a cloud service,
  organize them on the device with a compact image-text model, and share the small
  adapters learned from user corrections, so that each phone improves from its peers.
  **Type:** Research + Applied. (AlexT, RaduC)
- **T13. Federated Music Recommendation on Real Android Phones:** Research and
  develop an Android music recommender trained with federated learning, so that
  listening history never leaves the phone, and measure on real phones how
  recommendation quality, battery use, traffic, and training time compared with
  centralized training, including users with very different tastes. **Type:**
  Research + Applied. (AlexT, RaduC)

---

## **Resource-Efficient On-Device and Edge Federated AI**

Resource-efficient federated AI investigates how collaborative learning can operate on
smartphones, wearable devices, embedded systems, and edge nodes with limited
computation, memory, battery, and communication capacity. The research challenge is
not limited to minimizing model size: training frequency, synchronization,
representation choice, thermal constraints, network conditions, and device
heterogeneity must be considered jointly. Research in this direction develops
adaptive mechanisms that decide when, where, and how much learning or communication
should occur.

- **T1. Adaptive Local Training under Energy and Connectivity Constraints:** Research
  and develop mechanisms that dynamically select the number of local training epochs
  according to battery level, thermal state, model drift, bandwidth, and predicted
  device availability. **Type:** Research + Applied. (RaduC, AlexC, AlexT)
- **T2. Contact-Budget-Aware Compression of Federated Updates:** Research compression
  strategies that adapt the exchanged representation (gradients, parameters, sparse
  updates, prototypes, logits, or adapters) to the duration and quality of the
  available connection. **Type:** Research. (RaduC, AlexT)
- **T3. Dynamic Partitioning for Split and Federated Learning at the Edge:** Research
  methods that dynamically determine which model layers should execute on a mobile
  device and which should be offloaded to another device, an edge node, or the cloud,
  jointly optimizing accuracy, privacy, latency, and energy consumption. **Type:**
  Research + Applied. (RaduC, AlexC)
- **T4. Heterogeneous Federated Fine-Tuning of On-Device Language Models:** Research
  and develop federated fine-tuning mechanisms in which devices with different
  capabilities train different subsets of an LLM, such as LoRA adapters, prompts,
  attention heads, or model layers. **Type:** Research + Applied. (RaduC, RaduM)
- **T5. Real-Device Energy and Thermal Benchmarking for Federated AI:** Design and
  perform a systematic experimental study of federated training and inference on
  smartphones, Raspberry Pi, Jetson, and other edge platforms, measuring energy,
  latency, memory, communication, temperature, and throttling. **Type:** Research +
  Applied. (RaduC, RaduM, AlexT)
- **T6. Sustainable Client Selection in Federated Learning:** Research scheduling
  mechanisms that select participating devices based on learning utility, energy
  availability, carbon intensity, connectivity, and statistical representativeness
  rather than selecting clients randomly. **Type:** Research. (RaduC, AlexC)
- **T7. On-Device Image Segmentation for Field and Drone Imagery:** Research and
  develop lightweight segmentation models that run on smartphones, drones, or edge
  devices in areas with limited connectivity, studying the trade-off between model
  size, accuracy, energy consumption, and the amount of data that must be transmitted.
  **Type:** Research + Applied. (RaduM)
- **T8. Background Execution Limits for On-Device Learning:** Research how the rules
  that mobile operating systems and phone manufacturers impose on background work,
  such as battery-saving modes, affect when and how often a device can actually take
  part in collaborative training. **Type:** Research + Applied. (RaduM)
- **T9. A Cross-Platform Federated Learning Client for Android and iOS:** Research and
  develop a single mobile client, built with cross-platform technologies such as Kotlin
  Multiplatform, that can take part in federated training on both Android and iOS, and
  compare it with separate native implementations. **Type:** Research + Applied.
  (RaduM)
- **T10. Context-Aware Choice between On-Device and Server Inference:** Research and
  develop a policy that decides, for each AI request, whether to run it on the phone
  or on a server, using battery level, measured network quality, and thermal headroom
  together, and evaluate it on several real Android phones against always-local and
  always-server execution. **Type:** Research + Applied. (AlexT, RaduC)
- **T11. Crowdsourced Measurement of On-Device Training Cost:** Research and develop a
  benchmark application that volunteers install to measure inference and on-device
  training time, energy, memory, and heating for real models on CPU, GPU, and NPU, and
  publish the collected measurements as an open dataset. **Type:** Research +
  Applied. (AlexT, RaduC)
- **T12. Offline Scene Description in Romanian for Visually Impaired Users:** Research
  and develop an Android assistant that describes the camera view by voice, in Romanian
  and without an Internet connection, using a small vision-language model running on the
  phone, and evaluate response time, battery use, heating, and description quality on
  mid-range devices. **Type:** Research + Applied. (AlexT, RaduC)
- **T13. How Wearing Style Affects On-Watch Models, and How to Adapt to It:** The same
  smartwatch model, whether it recognizes gestures, workouts, or sleep, may behave
  differently depending on how the watch is worn: on which wrist, rotated around the
  forearm, tight or loose, or at different times of day. Research how much these
  differences affect the quality of several wearable models, and develop a Wear OS
  application that detects how the watch is being worn and uses this information to
  make the models more reliable, comparing it with simpler alternatives. Evaluate
  recognition quality per task, false detections, and the energy cost on the watch.
  **Type:** Research + Applied. (Alexandra, RaduC)
- **T14. Multi-Model Scheduling on Smartwatches:** Smartwatches may run several AI
  models continuously for tasks such as fall detection, gesture recognition, and sleep
  monitoring, despite having limited computing resources and battery capacity.
  Research scheduling strategies that balance task urgency, execution deadlines, and
  energy consumption, and investigate when sharing model components can reduce
  redundant computation. Evaluate the proposed strategies against independent model
  execution, measuring detection quality, response latency, and energy use on
  smartwatches. **Type:** Research + Applied. (Alexandra, RaduC)

---

## **Privacy, Robustness, and Fairness in Federated Edge Systems**

Federated learning reduces direct data sharing but does not automatically guarantee
privacy, security, robustness, or fairness. Model updates may disclose user identity,
location, activity, or sensitive attributes, while malicious participants may poison
models or insert backdoors. In decentralized environments, security is further
affected by communication topology, unequal device availability, and the absence of a
permanently trusted coordinator. Research in this area studies attacks, defenses,
secure aggregation, differential privacy, trust, rare-client representation, and
recovery from compromised updates.

- **T1. Topology-Induced Privacy Leakage in Decentralized Federated Learning:**
  Research how repeated and overlapping neighborhood aggregations may reveal
  individual model updates in sparse or temporal contact graphs, and develop
  topology-aware countermeasures. **Type:** Research. (RaduC, AlexT)
- **T2. Byzantine- and Backdoor-Resilient Opportunistic Federated Learning:** Research
  and develop lightweight mechanisms for detecting and limiting malicious updates when
  devices communicate only with local peers and no trusted global server is
  continuously available. **Type:** Research + Applied. (RaduC, RaduM, AlexT)
- **T3. Fair Federated Learning under Non-Uniform Device Availability:** Research
  mechanisms that prevent frequently connected devices from dominating the learned
  model and preserve the influence of users, locations, or mobility patterns that appear
  only rarely. **Type:** Research. (RaduC, AlexC)
- **T4. Privacy Leakage and Client Re-Identification from Mobility Updates:** Evaluate
  whether federated updates generated from GPS, BLE, Wi-Fi, inertial, or transport data
  can be linked to individual users, and compare defenses based on clipping,
  differential privacy, aggregation, and representation learning. **Type:** Research +
  Applied. (RaduC, Alexandra)
- **T5. Federated Unlearning on Mobile and Edge Devices:** Research methods for
  removing the contribution of a user, device, location, or time interval from a
  federated model while minimizing retraining cost and preserving model utility.
  **Type:** Research + Applied. (RaduC, AlexC)
- **T6. Trust and Reputation for Decentralized Federated Collaboration:** Research
  context-aware trust models that evaluate encountered devices using update
  consistency, past interactions, topology, resource behavior, and suspected attacks,
  without permanently excluding devices affected only by temporary failures or
  distribution shifts. **Type:** Research + Applied. (RaduC, AlexT)
- **T7. Fault Tolerance in Federated Learning across Unstable Edge-to-Cloud
  Infrastructures:** Collaborative training can slow down or stop when participating
  devices fail, lose connectivity, or respond too late. Investigate how a federated
  learning system can keep making progress despite these ordinary infrastructure
  problems. Compare recovery, timeouts, and client-replacement strategies under
  controlled failures, separating accidental faults from deliberate attacks. The focus
  is on reliable execution in realistic deployments rather than trust or reputation
  between mobile peers. **Type:** Research + Applied. (AlexC, RaduC)
- **T8. Distinguishing Malicious Model Updates from Naturally Different Client Data:**
  In federated learning, clients often contribute different kinds of data, so their
  model updates can look unusual even when they are legitimate. Study how to tell
  apart differences caused by local data and updates that have been deliberately
  corrupted. Compare clustering, small-group aggregation, and robust aggregation
  strategies, measuring both attack resistance and the risk of wrongly excluding honest
  clients. The emphasis is on data heterogeneity and detection accuracy, not on
  opportunistic network topology. **Type:** Research. (AlexC)
- **T9. Robust Federated Learning with Streaming Data and Changing Participants:**
  Real-world datasets evolve as new measurements arrive, while devices may join or leave
  training at any time. Explore how these changes affect the quality and reliability of
  a federated model. Design and test methods that detect shifts in local data, update
  groups of similar clients, or adjust training as conditions change. A possible use
  case is environmental sensing, where both observations and sensor availability vary
  over time. **Type:** Research + Applied. (AlexC)
- **T10. Consent Management and Revocation in Collaborative Learning:** Research and
  develop mechanisms through which users grant, monitor, and revoke access to their
  data, and study how a revocation should propagate to models that were already trained
  on that data. **Type:** Research + Applied. (RaduM)
- **T11. Decentralized Identity for Federated Participants:** Research how devices and
  organizations can prove their identity and attributes using verifiable credentials,
  allowing trusted participation in federated learning without relying on a central
  identity provider. **Type:** Research. (RaduM)
- **T12. Screening a Model Received from a Single Peer:** Robust aggregation needs
  several updates to compare, but at an encounter a phone receives only one. Research
  lightweight checks that a device can run on a single received model, such as testing
  it on a small local validation set or comparing the direction of the update with its
  own. **Type:** Research + Applied. (AlexT, RaduC)
- **T13. Membership Inference in One-to-One Model Exchanges:** When a model is sent
  directly to one peer, no aggregation hides the sender's contribution. Research what a
  peer can infer about the sender's data from models received during encounters, and
  evaluate defenses such as clipping, noise, or sending only parts of the model.
  **Type:** Research. (AlexT, RaduC)
- **T14. Collaborative On-Device Detection of Fraudulent SMS in Romanian:** Research
  and develop an Android classifier that detects fraudulent SMS messages in Romanian
  directly on the phone, and study how phones can learn new scam campaigns through
  federated learning without uploading message content. **Type:** Research + Applied.
  (AlexT, RaduC)

---

## **Federated AI for Green Transportation and Sustainable Mobility**

Federated AI for green transportation investigates how mobility stakeholders,
vehicles, travelers, mobile devices, roadside infrastructure, and public-transport
operators can collaboratively learn models without centralizing sensitive mobility
data. These models can support modal-shift analysis, traffic and demand forecasting,
eco-routing, public-transport optimization, electric-vehicle infrastructure, and
emission reduction. A central research challenge is to combine heterogeneous and
non-IID data while accounting for privacy, intermittent connectivity, organizational
boundaries, energy consumption, and the unequal representation of mobility patterns.

- **T1. Federated Recognition of Transportation Modes:** Research and develop
  privacy-preserving models that recognize walking, cycling, public transport, private
  cars, and shared mobility using smartphone, wearable, GPS, inertial, or contextual
  data distributed across users. **Type:** Research + Applied. (RaduC, AlexT)
- **T2. Cross-Silo Federated Mobility and Transport-Demand Forecasting:** Research
  methods through which universities, transport operators, municipalities, and
  mobility-service providers collaboratively predict passenger flows or transport
  demand without exchanging their raw datasets. **Type:** Research + Applied. (RaduC)
- **T3. Personalized Federated Eco-Routing:** Research and develop routing mechanisms
  that learn user preferences locally while optimizing travel time, energy
  consumption, emissions, congestion, and the use of sustainable transportation modes.
  **Type:** Research + Applied. (RaduC, AlexT)
- **T4. Opportunistic Federated Learning for Sustainable Travel Recommendations:**
  Research how nearby smartphones, vehicles, and transport infrastructure can exchange
  compact knowledge during encounters to improve local recommendations when continuous
  cloud connectivity is unavailable or undesirable. **Type:** Research + Applied.
  (RaduC, AlexT)
- **T5. Federated Prediction of Electric-Vehicle Charging and Parking Demand:**
  Research models that combine private vehicle histories, charging-station
  observations, parking occupancy, weather, events, and traffic information to predict
  spatial and temporal demand. **Type:** Research + Applied. (RaduC, Alexandra)
- **T6. Federated Edge Intelligence for Traffic and Emission Anomaly Detection:**
  Research and develop distributed methods that allow roadside cameras, environmental
  sensors, vehicles, and campus edge nodes to detect congestion, incidents, abnormal
  emissions, or unsafe mobility patterns without transferring all raw data. **Type:**
  Research + Applied. (RaduC, AlexT)
- **T7. Federated Mobility Digital Twin for Evaluating Green Policies:** Research and
  develop a Digital Twin in which locally trained mobility models are integrated to
  simulate modal shifts, traffic interventions, parking policies, charging
  infrastructure, or low-emission scenarios. **Type:** Research + Applied. (RaduC)
- **T8. Fairness and Inclusion in Federated Sustainable-Mobility Models:** Research
  whether federated mobility models systematically underrepresent pedestrians,
  cyclists, people with limited mobility, uncommon routes, or participants with
  infrequent connectivity, and develop appropriate fairness metrics and aggregation
  mechanisms. **Type:** Research. (RaduC, Alexandra)
- **T9. Reproducible System-Level Evaluation of Federated AI for Smart Mobility:**
  Mobility applications may use federated learning to predict passenger demand or
  traffic conditions without collecting all raw data in one place. Study how network
  delays, uneven device performance, and changing participant availability influence
  the real cost of training such models. Build a repeatable set of experiments and
  compare simplified simulations with realistic Edge-to-Cloud conditions, measuring
  prediction quality, runtime, network traffic, and energy use. The focus is on
  experimental methodology rather than developing a new mobility prediction algorithm.
  **Type:** Research + Applied. (AlexC)
- **T10. Crowdsourced Estimation of Public Transport Occupancy:** Research how
  passengers’ smartphones can collaboratively estimate how crowded buses, trams, or
  metro cars are without revealing who is travelling, and how these estimates can help
  travelers choose less crowded options. **Type:** Research + Applied. (RaduM, RaduC)
- **T11. Crowdsourced Mapping of Accessibility Barriers:** Research and develop
  methods through which phone users report and confirm obstacles such as missing ramps,
  blocked sidewalks, or broken elevators, and use these reports to suggest suitable
  routes for people with limited mobility. **Type:** Research + Applied. (RaduM)
- **T12. Smartphone Sensing of Road and Cycling Infrastructure:** Research and develop
  methods through which phones carried by cyclists and drivers detect problems such as
  potholes or unsafe road segments, learning collaboratively without uploading raw
  sensor data. **Type:** Research + Applied. (RaduM)
- **T13. Opportunistic Sharing of Transport-Mode Models between Commuters:** People on
  the same bus, tram, or metro stay close for minutes. Research and develop a mechanism
  through which their phones exchange transport-mode recognition models during the
  ride, and compare the result with server-based federated training. **Type:** Research
  + Applied. (AlexT, RaduC)

---

## **Explainable, Traceable, and Trustworthy AI**

AI models can produce accurate predictions while leaving important questions
unanswered: which information influenced a prediction, how was the result produced, and
will the explanation still make sense when the data or the model change? Explainable AI
(XAI) explores complementary approaches, from identifying influential inputs and
interpreting predictions through human-understandable concepts to generating realistic
“what-if” alternatives. Data provenance adds another perspective by tracing the
datasets, processing steps, and model versions behind a result. This research area
studies both how explanations can be produced and how useful and reliable they are,
with possible applications in environmental monitoring and biomedical research.

- **T1. Provenance-Aware Analysis of AI Workflows and Results:** An AI result depends
  not only on the model, but also on its input data and the processing pipeline.
  Explore how information about datasets, preprocessing steps, model versions, and
  workflow executions can be recorded and visualized. Develop a lightweight prototype
  that helps researchers trace a result back to its origins and compare two
  experimental runs. Study how this end-to-end traceability complements explanations of
  individual model predictions. **Type:** Research + Applied. **Research context:**
  Collaboration with Inria France (AlexC)
- **T2. Detecting and Characterizing Explanation Drift in Evolving AI Systems:** When
  new data arrive or a model is updated, its predictions (and the information it relies
  on) may change, even if overall accuracy remains similar. Investigate how
  explanations, such as feature-attribution scores, evolve across different time
  periods or model versions. Develop a small evaluation or monitoring prototype to
  identify and visualize meaningful changes in model behavior. Environmental sensor
  observations or other openly available time-series data can provide a concrete use
  case. **Type:** Research + Applied. (AlexC)
- **T3. Concept-Based Interpretability for Scientific Machine Learning:** A list of
  influential features is not always meaningful to someone working with scientific data.
  Explore methods that describe model predictions using understandable concepts, such
  as sustained warming, unusual sensor patterns, or recognizable image characteristics.
  One can investigate approaches such as Concept Activation Vectors or Concept
  Bottleneck Models on a manageable public dataset. Compare the resulting explanations
  with conventional feature-attribution methods and study how accurately they reflect
  the model’s behavior. Possible use cases: environmental, medical applications.
  **Type:** Research + Applied. (AlexC)
- **T4. Constraint-Aware Counterfactual Explanations for AI Predictions:**
  Counterfactual explanations ask how an input would need to change for an AI model to
  produce a different prediction. Explore ways to generate informative “what-if”
  examples while respecting realistic constraints (for instance, keeping sensor
  readings within feasible ranges or avoiding inconsistent combinations of variables).
  Build a small prototype for an environmental prediction task or another public
  dataset, and evaluate the validity, simplicity, and plausibility of its explanations.
  These model-based alternatives should not be presented as proof of cause and effect.
  Possible use case: environmental monitoring. **Type:** Research + Applied. (AlexC,
  RaduC)
- **T5. Tracking the Provenance of Models Built through Device-to-Device Exchanges:**
  Research lightweight mechanisms that record which devices contributed to a model as
  it travels through encounters, so that a harmful contribution can be traced and
  removed later, without revealing who met whom. **Type:** Research. (AlexT, RaduC)

---

## **Reproducible and Reliable Evaluation of Distributed AI**

An AI method that works well on one computer may behave very differently when deployed
across several sites with different hardware and network conditions. Even running the
same experiment twice can lead to different results if its data, configuration,
infrastructure, and software environment are not properly recorded. This research
area studies how to design fair comparisons, reproduce experiments, and understand
where performance differences come from. Students may work with emulation, experiment
automation, performance monitoring, and distributed testbeds such as Grid’5000 or
Chameleon. Access to such platforms is granted through the team’s ongoing
collaborations with Inria (France), Argonne National Laboratory (USA) and Oak Ridge
National Laboratory (USA).

- **T1. Evaluating Federated Learning through Realistic Edge-to-Cloud Emulation:** A
  federated learning algorithm may look efficient in a simulator but behave
  differently on machines spread across multiple sites. Build a repeatable
  experimental setup that introduces realistic network delays, varying bandwidth, and
  differences in computing power. Compare analytical or simulation-based estimates with
  emulated and distributed executions, tracking training time, communication, energy,
  and model quality. The emphasis is on system-level experiment fidelity and
  reproducibility, not on benchmarking the battery or temperature of individual
  devices. **Type:** Research + Applied. **Research context:** Collaboration with
  Inria France (AlexC)
- **T2. Reproducible Benchmarking of Distributed AI Models and Learning Paradigms:**
  Two AI models or learning approaches should be compared under conditions that other
  researchers can understand and repeat. Identify which details must be captured (data
  partitions, random seeds, software versions, hardware, network settings, and
  metrics) and build an automated comparison workflow. Validate it using a small
  selection of AI applications on heterogeneous infrastructure. **Type:** Research +
  Applied. **Research context:** Collaboration with Inria and Oak Ridge National
  Laboratory (AlexC)
- **T3. Reproducing and Understanding Edge-to-Cloud Application Workflows:** Study how
  distributed application workflows can be deployed, measured, and repeatedly executed
  across Edge, Cloud, and HPC resources. Explore experimental orchestration frameworks
  (tools that automate infrastructure configuration, application deployment, execution,
  and performance monitoring) such as the open-source E2Clab platform or alternative
  tools with similar capabilities. Use a scientific monitoring or image-processing
  pipeline to compare infrastructure configurations and analyze end-to-end performance
  and reproducibility. **Type:** Research + Applied. **Research context:** Collaboration
  with Oak Ridge National Laboratory (AlexC)
- **T4. Quantifying Reproducibility under Dynamic Execution Conditions:** In a changing
  environment, an experiment may not produce exactly the same numbers every time.
  Explore how to define an acceptable range of variation for accuracy, runtime, energy,
  or other results, and how to detect when a new run falls outside it. The goal is to
  create a lightweight monitoring and comparison tool for repeated AI experiments.
  **Type:** Research + Applied. (AlexC)
- **T5. Consistency of On-Device AI across Different Phones:** Research whether the same
  AI model produces the same predictions, speed, and battery cost on phones from
  different manufacturers and generations, and develop methods to detect and reduce
  these differences before an application is released. **Type:** Research + Applied.
  (RaduM)

---

## **Efficient and Sustainable AI across the Computing Continuum**

Modern applications can run on a wide range of computing resources: sensors and small
edge devices, nearby servers, public clouds, and supercomputers. This connected
environment is often called the computing continuum. Choosing where each part of an
application should run is important: processing data close to a sensor may reduce
delay and network traffic, while powerful remote systems may train models faster. This
research area investigates how to balance application quality, execution time, energy
use, communication overhead, and infrastructure cost when designing and running
distributed AI workflows.

- **T1. Understanding the Performance Trade-offs of Distributed AI Approaches:** Compare
  selected machine-learning approaches (such as federated, online, or reinforcement
  learning) under different computing and networking conditions. Study how design
  choices affect model quality, training or inference time, energy use, and data
  movement. Rather than combining every paradigm at once, the project will focus on a
  clearly defined comparison and a small number of measurable trade-offs. **Type:**
  Research. (AlexC)
- **T2. Adaptive Task Placement for AI Workflows across the Computing Continuum:**
  Explore how an application can decide whether a processing step should run near the
  data source, on an edge server, in the cloud, or on HPC infrastructure. Build a
  simple placement strategy that considers network delay, available resources, and
  data transfer volume. A possible use case is a monitoring pipeline that turns
  environmental sensor measurements into predictions or alerts. **Type:** Research +
  Applied. (AlexC, RaduC)
- **T3. Energy-Aware Scheduling of Distributed AI Workflows:** Running the same AI
  pipeline on different machines can lead to very different energy costs. Investigate
  simple scheduling policies that select resources using both performance and energy
  measurements. Compare the policies against common baselines and identify when
  reducing energy consumption comes at the cost of longer execution time. **Type:**
  Research + Applied. (AlexC, RaduC)
- **T4. Energy Cost of Decentralized versus Server-Based Federated Learning:** Research
  the total energy needed to reach the same accuracy with server-based federated
  learning and with device-to-device learning, counting phones, radio transfers, and
  servers, and identify when each approach is more efficient. **Type:** Research.
  (AlexT, RaduC)

---

## **Continual Learning and Adaptive Language Models**

Traditional AI models are usually trained on a fixed dataset and then deployed. In
practice, new information arrives continuously: scientific observations accumulate,
user needs change, and documents are updated. Updating a model is challenging because
learning something new can make it forget previously learned information, a problem
known as catastrophic forgetting. Language models face a related choice: should they be
fine-tuned on new information, or should they retrieve that information when
answering a question? This research area examines efficient ways to manage evolving
knowledge, including replay-based training, distributed learning, fine-tuning, and
retrieval-based approaches.

- **T1. Scalable Replay-Based Continual Learning for Mitigating Catastrophic
  Forgetting:** When AI models learn from new data, they may lose knowledge acquired
  during previous training stages, a phenomenon known as catastrophic forgetting. This
  is a major challenge for applications that must continuously adapt to new
  information. Investigate replay-based methods that preserve previously learned
  knowledge by reusing selected past examples during training. Explore parallel and
  distributed training strategies to reduce execution time and memory overhead while
  maintaining accuracy on both old and new tasks. **Type:** Research + Applied.
  **Research context:** Collaboration with Argonne National Laboratory, USA (AlexC)
- **T2. Smarter Replay Buffers for Data-Parallel Continual Learning:** In continual
  learning, AI models must learn from new data while preserving knowledge acquired from
  previous tasks. One common approach is to maintain a replay buffer, a small collection
  of representative examples from previously encountered data, which are periodically
  reused during training to reduce catastrophic forgetting. This research investigates
  how these examples can be efficiently selected, stored, and updated when training is
  distributed across multiple computing nodes. Explore strategies for managing replay
  buffers in data-parallel environments, balancing memory usage, training efficiency,
  and model accuracy. **Type:** Research + Applied. **Research context:** Collaboration
  with Argonne National Laboratory, USA (AlexC)
- **T3. Mitigating Catastrophic Forgetting in Continual Fine-Tuning of Language
  Models:** Large Language Models (LLMs) often need to be updated with new knowledge or
  adapted to new tasks. However, repeatedly fine-tuning a model can lead to
  catastrophic forgetting, where learning new information degrades previously acquired
  capabilities. Investigate how continual fine-tuning can be combined with replay
  mechanisms that preserve representative examples from earlier training stages.
  Explore efficient fine-tuning techniques and distributed data management strategies
  to reduce forgetting while keeping computational and memory costs manageable.
  **Type:** Research + Applied. **Research context:** Collaboration with Argonne
  National Laboratory, USA (AlexC)
- **T4. Retrieval-Augmented In-Context Learning with Distributed Example Buffers:**
  Large Language Models can adapt to new tasks by incorporating relevant information
  directly into their input context, without updating model parameters. Investigate how
  distributed collections of previously encountered examples can support this process
  through retrieval-based selection. Develop methods for identifying and retrieving
  relevant examples using semantic similarity and dynamically incorporating them into
  the model's context. Evaluate the impact of retrieval strategies on response quality,
  context utilization, scalability, and inference latency. **Type:** Research +
  Applied. **Research context:** Collaboration with Argonne National Laboratory, USA
  (AlexC)
- **T5. Fine-Tuning or Retrieval: How Should an AI System Learn New Information?**
  This topic aims to compare two practical ways of adapting a language model to updated
  knowledge: lightweight fine-tuning and retrieval-augmented generation. Use a
  collection of documents that changes over time, and measure answer quality, update
  cost, memory needs, and response latency. The goal is to identify when each strategy
  is more suitable, rather than assuming one always wins. **Type:** Research +
  Applied. (AlexC)
- **T6. Notification Prioritization Learned on the Phone:** Research and develop an
  Android application that learns from which notifications the user opens or ignores
  and ranks them by importance, comparing a model that keeps learning on the phone with
  fixed rules and with a language model used without training. **Type:** Research +
  Applied. (AlexT, RaduC)

---

## **Quantum-Classical Computing and Workflow Integration**

Quantum computers are increasingly accessible through cloud services and research
infrastructures, but most useful applications still involve substantial classical
computation. A hybrid workflow may repeatedly prepare data on a CPU or GPU, submit a
quantum circuit, collect its results, and update a classical algorithm. Connecting
these steps raises practical questions about interfaces, job scheduling, data
transfers, reliability, and performance. This research area focuses on the software and
systems needed to integrate quantum processing into existing cloud and HPC workflows,
not on building quantum hardware or requiring advanced quantum physics from the outset.

- **T1. Connecting Quantum Programs to Cloud and HPC Workflows:** Study how applications
  coordinate classical processors with quantum simulators or quantum processing
  services. Build a small workflow that submits quantum tasks, handles results, and
  records execution metadata, while examining differences between available software
  interfaces. Identify practical bottlenecks such as job submission, queueing, data
  exchange, and repeated classical-quantum interaction. **Type:** Research + Applied.
  (AlexC)
- **T2. Benchmarking the Cost of Hybrid Quantum-Classical Execution:** A quantum circuit
  may execute quickly, but a complete application can spend much more time preparing
  inputs, waiting for a backend, or processing results. Develop a reproducible
  benchmark that measures these steps using simulators and, where accessible, a cloud
  QPU. Compare end-to-end time, variability, and data movement rather than reporting
  circuit execution time alone. **Type:** Research + Applied. (AlexC)

---

## **Scalable Scientific Data Platforms for Environmental and Biomedical Research**

Scientific projects increasingly collect large and diverse datasets that must remain
useful for years and be shared by researchers with different needs. In BioMedLake,
hospitals and research institutions contribute clinical and genomic data to a secure
data-lake and HPC ecosystem. In DANUBIUS-RO, environmental observations and analysis
support research on rivers, deltas, and coastal areas. Both settings raise important
computer-science questions: how can data be collected reliably, stored efficiently,
found quickly, processed at scale, and traced back to its origin? These topics focus on
data engineering and distributed systems, using public or synthetic datasets when
access to project data is restricted.

- **T1. Building Efficient Data Ingestion Pipelines for Biomedical Research:** Design
  and evaluate a pipeline that collects data from different sources, checks basic
  quality rules, transforms it into a consistent format, and stores it for later
  research. Use synthetic or public clinical datasets with heterogeneous schemas to
  measure throughput, processing delays, failure recovery, and the cost of data
  transformations. **Type:** Research + Applied. (AlexC)
- **T2. Smart Storage and Data Lifecycle Management for a Medical Data Lake:** Not all
  research data are accessed equally often, and keeping everything on high-performance
  storage can be expensive. Compare strategies for organizing datasets, choosing
  storage formats, compressing data, and moving less frequently used data to cheaper
  storage tiers. Build a prototype and evaluate storage footprint, retrieval time, and
  cost. **Type:** Research + Applied. (AlexC)
- **T3. Versioned and Traceable Research Datasets in a Medical Data Lake:** Researchers
  need to know exactly which dataset version they used and how it was prepared. Design a
  prototype that records dataset versions, transformations, access permissions, and
  links between source data and derived results. Explore how to support reproducible
  queries without exposing sensitive information. Evaluation should use public or
  synthetic data unless authorized access is available. **Type:** Research + Applied.
  (AlexC)
- **T4. Reliable Streaming Pipelines for Environmental Monitoring:** Environmental
  sensors can produce continuous measurements of water quality, weather, or river
  conditions. Build a streaming pipeline that collects and processes incoming
  observations while coping with late, missing, or duplicated records. Evaluate how
  checkpointing, buffering, and recovery mechanisms affect accuracy and processing
  delay. **Type:** Research + Applied. (AlexC)
- **T5. Efficient Data Placement for River-to-Sea Monitoring Applications:** When
  observations come from multiple locations, transferring all data to a central cloud
  may be slow or costly. Compare processing near the sensors with remote processing,
  and investigate which data should be transferred, cached, or aggregated. Evaluate
  end-to-end delay, bandwidth consumption, and resource usage with representative
  environmental workloads. **Type:** Research + Applied. (AlexC, RaduC)
- **T6. Detecting Data Quality Problems in Environmental Observations:** Faulty sensors,
  missing measurements, and sudden shifts can create misleading patterns in scientific
  datasets. Develop a lightweight approach to flag suspicious observations and trace
  which processing steps may have introduced errors. Evaluate whether it improves the
  reliability of downstream analyses or early-warning pipelines, without confusing
  genuine environmental events with measurement failures. **Type:** Research +
  Applied. (AlexC)

---

## **Federated AI and Trusted Data Sharing in Data Spaces**

Data spaces are infrastructures in which organizations share data while keeping control
over who may use it, for what purpose, and under which conditions. They are being built
across Europe for domains such as agriculture, health, and mobility, relying on common
standards for identity, metadata, contracts, and data exchange. Combining data spaces
with AI raises new research challenges: training models on data that cannot be moved,
offering AI as a governed service, describing datasets so they can be discovered and
reused, and ensuring that usage conditions remain respected after data has been turned
into models or predictions.

- **T1. Federated Learning across Data Space Participants:** Research and develop
  mechanisms through which several organizations train a shared model, for example for
  crop or field image analysis, while their data never leaves their own infrastructure
  and every exchange follows an agreed sharing contract. **Type:** Research + Applied.
  (RaduM, RaduC)
- **T2. AI Models as Services in Data Spaces:** Research and develop ways to offer AI
  models, such as image analysis, as services that other participants can invoke through
  data space infrastructure, including long-running requests and the controlled return
  of results under the same usage conditions. **Type:** Research + Applied. (RaduM)
- **T3. Measuring the Cost of Data Sovereignty:** Design and perform an experimental
  study measuring the latency, communication, and resource overhead introduced by
  identity verification, contract negotiation, and access control, compared with
  direct data transfer. **Type:** Research + Applied. (RaduM)
- **T4. Automated Quality Assessment of Dataset Descriptions:** Research and develop
  tools that check whether dataset descriptions follow European metadata standards,
  report errors for each data source, and automatically suggest corrections. **Type:**
  Applied. (RaduM)
- **T5. LLM-Assisted Semantic Annotation of Datasets:** Research how large language
  models can link dataset descriptions and labels to shared vocabularies and thesauri,
  evaluating their accuracy against expert annotations across domains and languages.
  **Type:** Research + Applied. (RaduM)
- **T6. Machine-Enforceable Usage Policies for AI Training:** Research how data usage
  conditions, such as “may be used for training but not redistributed”, can be expressed
  formally and checked automatically during model training, aggregation, and sharing.
  **Type:** Research. (RaduM)
- **T7. Data Lineage in AI Pipelines:** Research and develop provenance-tracking
  mechanisms that keep annotations, trained models, and predictions traceable to the
  original datasets and the conditions under which they were shared. **Type:** Research
  + Applied. (RaduM)
- **T8. Mobile and Field Devices as Data Space Participants:** Research how
  smartphones, drones, and field sensors can contribute data to a data space under
  agreed usage conditions, even when they are only occasionally connected to the
  network. **Type:** Research + Applied. (RaduM, RaduC)
- **T9. Data Sharing between Public Institutions:** Research and develop ways for city
  halls, public utilities, and other institutions to exchange information about related
  problems, such as a broken water pipe under a damaged road, while each keeps control
  over its own data. **Type:** Research + Applied. (RaduM, RaduC)

---

## **AI for Digital Public Services**

Digital public services let citizens report problems, submit requests, and communicate
with local administrations through mobile and web applications. As these platforms
grow, administrations receive large numbers of requests that are often incomplete,
duplicated, or sent to the wrong department. Research in this area studies how AI and
distributed systems can help understand, organize, and resolve these requests, while
keeping the process transparent, fair, and respectful of citizens’ privacy.

- **T1. Automatic Categorization of Citizen Reports from Photos and Text:** Research
  and develop models that suggest the correct category of a reported problem, such as a
  pothole, illegal parking, or a broken street light, from its photo and description,
  and study how to handle reports that fit several categories. **Type:** Research +
  Applied. (RaduM, RaduC)
- **T2. Detecting Duplicate Reports of the Same Problem:** Research methods that
  recognize when several people report the same problem by combining location, time,
  photo similarity, and text, so that related reports can be grouped and handled
  together. **Type:** Research + Applied. (RaduM)
- **T3. Routing and Prioritizing Requests in Public Administrations:** Research and
  develop mechanisms that forward each request to the responsible department and
  estimate its urgency, learning from how similar requests were handled in the past.
  **Type:** Research + Applied. (RaduM, RaduC)
- **T4. Predicting Resolution Time for Citizen Requests:** Research models that
  estimate how long a reported problem will take to solve, based on its type, location,
  season, and current workload, and how such estimates can help administrations detect
  delays early. **Type:** Research + Applied. (RaduM)
- **T5. Summarizing Citizen Conversations with Language Models:** Research how
  language models can summarize long message threads about a request, highlight what is
  still unresolved, and suggest replies, evaluating their accuracy and the risk of
  incorrect or invented information. **Type:** Research + Applied. (RaduM)
- **T6. Collaborative Learning across Cities without Sharing Citizen Data:** Research
  how several municipalities can jointly train models, for example for report
  categorization, while each city’s data stays on its own servers, and how differences
  between cities affect the shared model. **Type:** Research. (RaduM)
- **T7. Citizen Reporting Application with On-Device Classification and
  Anonymization:** Research and develop an Android application that suggests the
  category of a reported problem directly on the phone and blurs faces and licence
  plates in the photo before upload, evaluating accuracy, latency, and how much personal
  information still reaches the administration. **Type:** Research + Applied. (AlexT,
  RaduC)
- **T8. Delay-Tolerant Citizen Reporting during Network Outages:** After a storm, flood,
  or power failure, the mobile network may be down exactly when problems must be
  reported. Research and develop a mechanism through which phones store reports, pass
  them to other phones they meet, and deliver them as soon as one of them reaches a
  connection, prioritizing urgent reports on the way. **Type:** Research + Applied.
  (AlexT, RaduC)
