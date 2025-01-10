# Mask9Leak1

A demonstration tool revealing how traditional data masking techniques, while protecting 9 out of 10 entities, consistently fail to secure that critical 1 in 10. This repository provides concrete evidence of masking vulnerabilities and re-identification risks in real-world scenarios.

## Why Mask9Leak1?

The name reflects a crucial reality in data privacy:
- For every 10 masked entities, 1 typically remains vulnerable
- Traditional masking techniques create a false sense of security
- Even a 10% leak rate can lead to significant privacy breaches
- One leaked entity can compromise an entire dataset

## Features

- **Multi-Layer Entity Detection**:
  - BERT-based Named Entity Recognition for PER (Person), ORG (Organization), and LOC (Location)
  - Regex-based detection for structured PII:
    - Social Security Numbers (SSN)
    - Driver's License Numbers
    - Vehicle Identification Numbers (VIN)
    - Bitcoin Addresses
    - Email Addresses

- **Vulnerability Demonstration**:
  - Shows how context can defeat masking
  - Demonstrates entity correlation attacks
  - Reveals pattern preservation issues
  - Exposes frequency analysis vulnerabilities

- **Batch Processing System**:
  Processes JSONL files with intermediate outputs at each stage:

  1. `1_original.jsonl` (Original Content):
  ```jsonl
  {"category": "Customer Service", "text": "Dear John Smith, Your order #12345 from Apple Store in Seattle has been shipped."}
  {"category": "Account", "text": "Contact support@apple.com or SSN: 123-45-6789 for verification."}
  ```

  2. `2_bracketed.jsonl` (Entity-Marked):
  ```jsonl
  {"category": "Customer Service", "text": "Dear [John Smith], Your order #12345 from [Apple Store] in [Seattle] has been shipped."}
  {"category": "Account", "text": "Contact [support@apple.com] or SSN: [123-45-6789] for verification."}
  ```

  3. `3_final_output.jsonl` (Anonymized):
  ```jsonl
  {"category": "Customer Service", "text": "Dear Michael Brown, Your order #12345 from Tesla Store in Portland has been shipped."}
  {"category": "Account", "text": "Contact support@techcorp.com or SSN: 987-65-4321 for verification."}
  ```

  Key Features:
  - Maintains consistency of replacements across documents
  - Preserves document structure and formatting
  - Retains original categorization
  - Processes in configurable batch sizes for memory efficiency

## Install
pip install -r requirements.txt

## Quick Start
replace the model path in the code with your own model path.
in the first step
```python
llm = LLM(
    model="/path_to_your_model/Qwen/Qwen2.5-7B-Instruct",
    tensor_parallel_size=1,  # Adjust based on your GPU setup
    trust_remote_code=True,
    max_model_len=2048
)
```

## PII Leakage Detection Tool
![image](https://github.com/user-attachments/assets/da851a15-3aab-4fcd-b3fa-de4bdec96e3b)

Find our professional PII leakage detection tool on AWS Marketplace:

### AWS Marketplace Listing
- **Product Name**: Mask9Leak1 Professional
- **Publisher**: [Your Company Name]
- **Category**: Security & Privacy Tools
- **Link**: [AWS Marketplace Link]

### Professional Features
1. **Advanced Detection Dashboard**:
   - Real-time PII leakage monitoring
   - Visualization of leakage patterns

2. **Enterprise Batch Processing**:
   ```jsonl
   // Input: Potentially compromised data
   {"text": "Contact john.smith@company.com (SSN: 123-45-6789)"}
   
   // Detection Output:
   {
     "text": "Contact john.smith@company.com (SSN: 123-45-6789)",
     "leaks": [
       {
         "type": "EMAIL",
         "value": "john.smith@company.com",
         "context": "Contact information"
       },
       {
         "type": "SSN",
         "value": "123-45-6789",
         "context": "Sensitive identifier"
       }
     ]
   }
   ```

3. **Compliance Reporting**:
   - GDPR compliance checks
   - HIPAA violation detection
   - PCI DSS monitoring

### Getting Started
1. Visit our listing on AWS Marketplace
2. Subscribe to the service
3. Follow integration documentation
4. Start monitoring for PII leaks

For more information, contact: [Your Contact Information]



