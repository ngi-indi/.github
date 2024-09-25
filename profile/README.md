  # INDI

  ![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
  ![Version 0.1](https://img.shields.io/badge/version-0.1-green.svg)
  ![Status: Stable](https://img.shields.io/badge/status-stable-brightgreen.svg)
  
The **INDI** (Improve Privacy and Trust in Non-Personalized Information Discovery) project is part of the **NGI Search** initiative funded by the **European Union** under grant agreement No. 101069364. INDI aims to create a **privacy-centric**, **transparent**, and **open-source** search engine with **debiasing**, **explainability**, and **anonymity** as core features. The project also includes a **crowdsourcing review platform** that leverages **human reviewers** to ensure search result quality through **manual validation**.

## Project Goals

The INDI project seeks to address key shortcomings in traditional search engines:

- **Bias and inequity**: Existing platforms often limit diverse perspectives and reinforce inequalities.  
  *INDI counters this by re-ranking results to prioritize debiasing, ensuring a diverse representation of perspectives.*

- **Opaque processes**: Users have limited insight into how search results are prioritized.  
  *INDI provides transparency through explainable artificial intelligence, offering users reasons for why certain results are ranked higher.*

- **Privacy invasion**: Search engines frequently track and exploit user data without consent.  
  *INDI enhances user privacy by anonymizing search queries and avoiding data collection, giving users control over their personal data.*

- **Erosion of trust**: These factors contribute to a lack of trust in search results.  
  *INDI seeks to rebuild trust by offering a decentralized, community-driven review process that ensures transparency in result validation.*

## Installation
## Installation Instructions

### Prerequisites

Before starting, ensure you have Docker and Git installed on your system.

### Step 1: Create Docker Network

First, create a Docker network that will be used by all the containers to communicate with each other.

```bash
docker network create indi_network
```

### Step 2: Set Up the Bias Manager Module

1. Clone the **Bias Manager** repository:

```bash
git clone https://github.com/ngi-indi/module-bias-manager  
cd ./module-bias-manager
```

2. Build the Bias Manager Docker image:

```bash
docker build -t biasmanager .
```

3. Run the Bias Manager container:

```bash
docker run -d --name biasmanager --network indi_network -p 5000:5000 biasmanager
```

### Step 3: Set Up the Search Engine Module

1. Clone the **Search Engine** repository:

```bash
git clone https://github.com/ngi-indi/module-search  
cd ../module-search
```

2. Build the Search Engine Docker image:

```bash
docker build -t searchengine .
```

3. Run the Search Engine container:

```bash
docker run -d --name searchengine --network indi_network -p 8080:8080 searchengine
```

### Step 4: Set Up the Frontend Module

1. Clone the **Review Frontend** repository:

```bash
git clone https://github.com/ngi-indi/module-annotation  
cd ../module-annotation/frontend
```

2. Build the Review Frontend Docker image:

```bash
docker build -t reviewfrontend .
```

3. Run the Review Frontend container:

```bash
docker run -d --name reviewfrontend --network indi_network -p 3000:3000 reviewfrontend
```

### Step 5: Set Up the Database

1. Build the MySQL Docker image:

```bash
docker build -t reviewdb .
```

2. Run the Review Database container:

```bash
docker run -d --name reviewdb --network indi_network -p 3306:3306 reviewdb
```

### Step 6: Set Up the Backend Module

1. Build the Review Backend Docker image:

```bash
docker build -t reviewbackend .
```

2. Run the Review Backend container:

```bash
docker run -d --name reviewbackend --network indi_network -p 1337:1337 reviewbackend
```

## Partners

<img src="https://www.unica.it/sites/default/files/styles/wide/public/2023-06/Logo_lungo_RGB_d0.png?itok=b_qHk7do" alt="University of Cagliari Logo" width="225"/>

**University of Cagliari**  
Key research partner with expertise in Information Retrieval (IR), Artificial Intelligence (AI), and Semantic Web.

<img src="https://lifeprojects.r2msolution.com/wp-content/uploads/2024/03/Logo-R2M-Solution-RED-SRGB-2.png" alt="R2M Solution Logo" width="100"/>

**R2M Solution**  
Business development partner providing industry experience on Information and Communication Technologies (ICT).

## How to Contribute

We welcome contributions from the open-source community, including code improvements, feedback on user experience, and participation in the review process. You can participate in validation tasks or suggest improvements to ensure INDI meets its goals of enhancing privacy, transparency, and trust in online information discovery.

## License
This project is licensed under the MIT License - see the [LICENSE](https://github.com/ngi-indi/.github/blob/main/LICENSE.md) file for details.

## Contact
For any questions or support, please reach out to:
- University of Cagliari: bart@unica.it, diego.reforgiato@unica.it, ludovico.boratto@unica.it, mirko.marras@unica.it
- R2M Solution: giuseppe.scarpi@r2msolution.com
- Website: Coming soon!

---

This project is funded within the framework of the NGI Search project. The views expressed here are those of the author(s) only and do not necessarily reflect the views of the European Union.
