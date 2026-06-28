# Public Artifact for the Paper

This repository is prepared for the public artifact accompanying the paper [*Optimizing NetGPT via Routing-Based Synergy and Reinforcement Learning*](https://arxiv.org/abs/2511.22217).

The paper studies LLM-based task planning and adaptive cloud-edge routing for federated-learning workflows. In the proposed framework, an edge LLM generates structured tool-calling actions, a reward/preference model scores candidate actions, and a routing module decides whether each step should be handled locally or escalated to a cloud LLM under dynamic network conditions. The framework further reuses cloud-routed samples to support reward-model refresh and edge-side policy improvement.

After the paper is accepted, we will release the public datasets and the main reference scripts used in the study.
