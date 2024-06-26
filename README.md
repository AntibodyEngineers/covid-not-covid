# COVID not COVID

The overall goal of the work is to demystify machine learning (ML). ML is a large area that encompasses many approaches and details are typically communicated at an expert level and include many terms from statistical methods, neural nets, convolutional neural nets, transformers.  Moreover, the common examples do not apply to the biotech world and often focus on how to sort dogs, cats, and check writing samples. We want to contextualize ML for biotech and get a small amount of practice. Toward the goal of demystifying ML we wanted to have projects where teams learn about input data, ML models, and what they [models] can and cannot do. In this work we trained an ML model that could interpret the protein sequence of an antibody to determine whether that antibody could bind to the receptor binding domain of the SARS-CoV-2 spike protein. To distinguish covid binding antibodies from non binders

## Resources
### Jetstream
We used the NSF supported Jetstream (https://jetstream-cloud.org/) computing resources. From the website: 
> Jetstream2 is a transformative update to the NSF’s science and engineering cloud infrastructure and provides 8 petaFLOPS of supercomputing power to simplify data analysis, boost discovery, and increase availability of AI resources. It is an NSF-funded, user-friendly cloud environment designed to allow “always on” research infrastructure and to give researchers access to interactive computing and data analysis resources on demand, whenever and wherever they want to analyze their data.

Jetstream provides the overall infrastructure. Users of the platform make computing resources available by creating virtual machines (VMs). A VM is a software instantiation of a computer that includes a number of GPU or CPU processors and a virtual disk of a specified size. Any number of VMs can be made. The size and type of the computer, how long it runs, and computing loads determines the number of SUs that are used. Jetstream provides web-based interfaces that allow one to configure VMs, set them to running, or shelve them. Shelved VMs are a way to preserve work without using SUs. 

For our case we estimated that we would need both GPU- (graphics processing unit) and CPU- (central processing unit) based computers. GPUs are used in high-performance computing applications. In the case of ML, computing models need to be trained on very large datasets and GPUs are often used for purpose. We estimated that our mix of GPUs and CPUs would require 120,000 SUs for a week's worth of operation (full uptime). 120,000 SUs were granted for one year. For the hackathon we set up one CPU and one GPU VM. Accounts were added for 10 team members. Over the course of the hackathon, and period afterward we used 73,000 of our 120,000 SU allocation.  

### Software
The python programming language and relevant python libraries were installed. The python libraries included machine learning packages such as tensorflow for computing and pandas for data preparation. In addition to the libraries, Jupyter notebook software (Jupyter lab) was installed to give team members a web-based interface to develop and share code. 

[Ablang](https://github.com/oxpig/AbLang) used for maching learning. It is an antibody specific language model trained on either the heavy or light chain antibody sequences from the [Observed Antibody Space](https://opig.stats.ox.ac.uk/webapps/oas/) database, or OAS. 
>OAS is a project to collect and annotate immune repertoires for use in large-scale analysis. It currently contains over one billion sequences, from over 80 different studies. These repertoires cover diverse immune states, organisms (primarily human and mouse), and individuals.

### Data Sets
Data from a companion database, [CoV-AbDab](https://opig.stats.ox.ac.uk/webapps/covabdab/) was used for training and testing. At the time (Aug 2022) the entire database contained about 10,000 entries. 

## What was Learned
The team included college instructors, high school teachers, students, and computational scientists. Some members had computing experience and were able to write scripts to clean data and work with the different python libraries. The project lead, worked as the technical lead and set up the computing environments. Only one of the team members had sufficient programming experience to build and test the ML prediction model. Other members were new to this kind of computing and using Jupyter Notebooks. Indeed, an unexpected outcome was that the Jupyter notebook instruction took a significant amount of time. 

With respect to ML prediction, a dataset of 4000 sequences containing the variable regions from neutralizing and non-neutralizing anti-SARS-CoV-2 spike protein were preprocessed into 768 attributes using the AbLang library. A first step in ML is to convert data into numerical n-dimensional vectors so that each datum is unique. Next the data are split into training data (3200 sequences) and test data (800 sequences). The training data are processed in the artificial neural network to build a model that distinguishes neutralizing sequences from non-neutralizing. The test data are then used to measure the model’s predictive quality. With 3200 training sequences our model had a 71% accuracy. On a 16 core CPU the model could be trained in five minutes. We were unable to test the GPU instance due to installation errors. 
  
Hackathons are funded by the National Science Foundation DUE 2055036

Work utalized the Jetstream2 resource:  
David Y. Hancock, Jeremy Fischer, John Michael Lowe, Winona Snapp-Childs, Marlon Pierce, Suresh Marru, J. Eric Coulter, Matthew Vaughn, Brian Beck, Nirav Merchant, Edwin Skidmore, and Gwen Jacobs. 2021. “Jetstream2: Accelerating cloud computing via Jetstream.” In Practice and Experience in Advanced Research Computing (PEARC ’21). Association for Computing Machinery, New York, NY, USA, Article 11, 1–8. DOI: https://doi.org/10.1145/3437359.3465565

Timothy J. Boerner, Stephen Deems, Thomas R. Furlani, Shelley L. Knuth, and John Towns. 2023. ACCESS: Advancing Innovation: NSF’s Advanced Cyberinfrastructure Coordination Ecosystem: Services & Support. “In Practice and Experience in Advanced Research Computing (PEARC ’23)”, July 23–27, 2023, Portland, OR, USA. ACM, New York, NY, USA, 4 pages. https://doi.org/10.1145/3569951.3597559

This work used Jetstream2 at Indiana University through allocation BIO220105 from the Advanced Cyberinfrastructure Coordination Ecosystem: Services & Support (ACCESS) program, which is supported by National Science Foundation grants #2138259, #2138286, #2138307, #2137603, and #2138296
