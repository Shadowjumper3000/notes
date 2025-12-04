## Perceptron Algorithm

A perceptron is a type of artificial neural network used for binary classification. It models a hyperplane that separates data into two classes. The perceptron algorithm iteratively adjusts its weights to correctly classify input data.

### **1. Understanding the Decision Boundary**

- A perceptron defines a decision boundary as a hyperplane in higher dimensions.
    
- In 2D space, a hyperplane is a line orthogonal to a weight vector.
    
- The weight vector determines the orientation of the decision boundary.
    

### **2. Perceptron Learning Algorithm**

1. **Initialize weights** randomly or set them to zero.
    
2. **For each training example (x, y):**
    
    - Compute the weighted sum:
        
    - Apply activation function: if , else
        
    - Compare the prediction with the actual label.
        
    - If the prediction is incorrect, update the weights:
        
    - is the learning rate.
        
3. **Repeat** until convergence (no weight updates required).
    

### **3. Update Rule**

- Adjust weights for misclassified data.
    
- If the perceptron misclassifies a point, it shifts the decision boundary to improve classification.
    
- The weight update ensures better classification over iterations.
    

### **4. Limitations of the Perceptron**

- Can only classify **linearly separable** data.
    
- Fails for XOR-type problems.
    
- Cannot learn complex decision boundaries without modifications (e.g., multi-layer perceptron).
    

Understanding the perceptron is fundamental for more advanced machine learning models such as deep neural networks.

