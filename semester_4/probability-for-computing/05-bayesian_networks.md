## Introduction to Bayesian Networks

- **Definition**: A Bayesian Network (BN) is a graphical model that represents probabilistic relationships among variables. It consists of nodes (representing random variables) and directed edges (representing conditional dependencies).
    
- **Components**:
    
    - **Nodes**: Represent random variables (can be observable quantities, latent variables, or hypotheses).
        
    - **Edges**: Represent conditional dependencies; an edge from node A to node B indicates that B is dependent on A.
        
    - **Conditional Probability Tables (CPTs)**: Each node has a CPT that quantifies the effect of the parents on the node.
        

## Key Concepts

- **Joint Probability Distribution**: BNs compactly represent the joint probability distribution of a set of variables. For variables X1,X2,…,XnX1​,X2​,…,Xn​, the joint distribution is given by:
    
    P(X1,X2,…,Xn)=∏i=1nP(Xi∣Parents(Xi))P(X1​,X2​,…,Xn​)=i=1∏n​P(Xi​∣Parents(Xi​))
- **Conditional Independence**: A key feature of BNs is that they encode conditional independence relationships. If two nodes are not connected, they are conditionally independent given their parents.
    
- **D-separation**: A criterion used to determine whether a set of nodes is independent of another set given a third set in the graph.
    

## Construction of Bayesian Networks

1. **Identify Variables**: Determine the relevant variables for the model.
    
2. **Define Structure**: Establish the directed acyclic graph (DAG) structure by identifying dependencies.
    
3. **Specify CPTs**: For each node, define the conditional probabilities given its parents.
    

## Inference in Bayesian Networks

- **Exact Inference**: Algorithms like Variable Elimination and the Junction Tree Algorithm can compute exact probabilities.
    
- **Approximate Inference**: Methods like Monte Carlo simulations (e.g., Gibbs sampling) are used when exact inference is computationally infeasible.
    

## Applications of Bayesian Networks

- **Medical Diagnosis**: Modeling diseases and symptoms.
    
- **Risk Assessment**: Evaluating risks in finance and engineering.
    
- **Machine Learning**: As a part of probabilistic models and classifiers.
    
- **Decision Making**: Incorporating utilities and decision nodes for decision analysis.
    

## Advantages and Limitations

- **Advantages**:
    
    - Intuitive representation of complex probabilistic relationships.
        
    - Efficient inference algorithms.
        
    - Ability to incorporate prior knowledge and update beliefs with evidence.
        
- **Limitations**:
    
    - Learning the network structure from data can be challenging.
        
    - Computationally expensive for large networks.
        
    - Requires accurate CPTs, which may be difficult to obtain.
        

## Learning Bayesian Networks

- **Parameter Learning**: Estimating the CPTs from data, often using Maximum Likelihood Estimation (MLE) or Bayesian Estimation.
    
- **Structure Learning**: Inferring the network structure from data, which can be done using score-based or constraint-based methods.
    

## Tools and Software

- **Software**: Various software tools are available for working with BNs, such as:
    
    - **BayesNet Toolbox** for MATLAB.
        
    - **PyMC3** and **pgmpy** in Python.
        
    - **GeNIe** and **SMILE** for graphical model construction and analysis.
        

## Conclusion

Bayesian Networks are powerful tools for reasoning under uncertainty. They provide a framework for understanding complex systems and making informed decisions based on probabilistic relationships. Mastery of BNs involves understanding their theoretical foundations, construction, inference methods, and practical applications.

DAG (Directed Acyclic Graph)
CPT (Conditional Probability Table)

### Inference
- Calculating some usefull quantity from a probability model (joint probability distribution)

> What is the probability that it Rains?


