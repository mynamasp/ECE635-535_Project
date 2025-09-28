# ECE635/535 Project
# Smart Doorbell using Raspberry Pi and ML


## Team Members & Responsibilities

| Name | Role | Lead Responsibilities |
|------|------|----------------------|
| Siyoum Sadore | Hardware Setup Lead | Raspberry Pi configuration, camera module integration, hardware troubleshooting |
| Prasanna Sridhar | Software Development Lead | ML model implementation, TensorFlow Lite deployment, main application logic |
| Florian Strobel | Networking & Research Lead | Literature review, documentation, Python scripting, notification system |

## Motivation

The market for home security devices is expanding due to an increasing trend in the need for residential security solutions. A wide range of products is used, spanning from biometric access controls to smart camera systems. In many cases, these systems rely on machine learning techniques - such as facial recognition - that are computationally intensive, which necessitates the use of cloud-based services. This causes challenges related to privacy, third-party dependency and the requirement of a stable internet connection.

In this project, a low-cost and lightweight image recognition solution is introduced. The software is executed on a Raspberry Pi which allows the following advantages:

- **Edge computing**: The images are processed locally on the Raspberry Pi resulting in lower latency and faster response times
- **Privacy**: The images do not have to be sent to a cloud service which lowers the risk for potential privacy issues
- **Cost-effectiveness**: The use of affordable hardware combined with the elimination of cloud service fees provides a clear economic advantage over cloud-based alternatives

## Design Goals

### Primary Goals
- Deploy a lightweight machine learning model on Raspberry Pi for real-time face detection and recognition
- Classify detected individuals as "known" or "unknown" household members
- Achieve acceptable inference speed (< 2 seconds per detection) on edge hardware
- Maintain high accuracy (> 85%) for face recognition tasks
- Implement mobile notification system (SMS)

### Secondary Goals
- Log all detection events with timestamps and images

## Deliverables

### Core Deliverables

#### ML Model Deployment
- TensorFlow Lite model optimized for Raspberry Pi
- Face detection and recognition pipeline
- Embedding-based comparison system for known vs unknown classification

#### Hardware Integration
- Raspberry Pi setup with camera module
- Proper mounting and positioning system
- Power management and stability considerations

#### Software Application
- Python application for real-time inference
- Image capture and processing pipeline
- Classification and alert logic
- Mobile notification system (SMS)

#### Documentation
- Setup instructions
- Performance analysis and benchmarks
- Demonstration video showing system functionality

## System Architecture


### System Hardware Block Diagram
<img width="862" height="356" alt="RPi Smart Doorbell Hardware Block Diagram" src="https://github.com/user-attachments/assets/21c3aec2-c531-48df-ad6e-0c61dbf06d66" />


### System Process Flow
<img width="600" height="7000" alt="RPi Door Bell Flow Chart" src="https://github.com/user-attachments/assets/3a84f163-7670-4aa2-92d2-937e0beedacd" />


## Hardware Components

- Raspberry Pi 4 (4GB RAM recommended)
- Camera Module v2 (8MP, 1080p)
- MicroSD Card (32GB minimum, Class 10)
- Power Supply (5V, 3A USB-C)

## Software Stack

- **Operating System**: Raspberry Pi OS (64-bit)
- **ML Framework**: TensorFlow Lite 2.x
- **Programming Language**: Python 3.9+
- **Computer Vision**: OpenCV 4.x
- **Additional Libraries**: NumPy, Pillow, requests (for notifications)

## Hardware/Software Requirements

### Hardware Requirements

| Component | Specification | Purpose |
|-----------|---------------|---------|
| Raspberry Pi | Pi 4, 4GB RAM minimum | Main processing unit |
| Camera Module | v2 (8MP) or v3 (12MP) | Image capture |
| MicroSD Card | 32GB+, Class 10, A1 rated | Storage and OS |
| Power Supply | 5V/3A USB-C | Stable power delivery |

### Software Requirements

- Python >= 3.9
- TensorFlow Lite >= 2.10.0
- OpenCV >= 4.5.0
- NumPy >= 1.21.0
- Pillow >= 8.0.0
- requests >= 2.28.0

## Implementation Approach

### Face Recognition Pipeline

1. **Face Detection**: Use lightweight models (MobileNet-based) for initial face detection
2. **Feature Extraction**: Generate 128-dimensional embeddings using FaceNet-like architecture
3. **Similarity Comparison**: Compare embeddings using cosine similarity or Euclidean distance
4. **Threshold-based Classification**: Classify as known (similarity > 0.75) or unknown

### Model Selection Strategy

- **Primary**: MobileNetV2 + FaceNet embeddings (TensorFlow Lite optimized)
- **Backup**: MTCNN for face detection + simple CNN for recognition
- **Delivery Detection**: Custom trained model on delivery uniform/package dataset

## Project Timeline

### Week 1-2 (Sep 28 - Oct 11): Setup & Research Phase
- **Hardware Setup Lead**: Configure Raspberry Pi, install OS, test camera module
- **Software Lead**: Research ML models, set up development environment
- **Research Lead**: Literature review, collect reference dataset, design system architecture

### Week 3-4 (Oct 12 - Oct 25): Core Development
- **Hardware Lead**: Finalize mounting system, optimize camera positioning
- **Software Lead**: Implement face detection pipeline, convert models to TensorFlow Lite
- **Research Lead**: Collect and label training data for known faces, test notification systems

### Week 5-6 (Oct 26 - Nov 8): Integration & Testing
- **All Members**: Integration testing, performance optimization, bug fixes
- **Software Lead**: Implement classification logic and embedding comparison
- **Research Lead**: Test alert mechanisms, document performance metrics

### Week 7-8 (Nov 9 - Nov 22): Final Testing & Documentation
- **Hardware Lead**: Final hardware setup
- **Software Lead**: Code optimization
- **Research Lead**: Complete documentation, prepare final presentation

### Week 9 (Nov 23 - Nov 29): Presentation Preparation
- **All Members**: Final testing, video creation, presentation preparation

## Expected Challenges & Solutions

### Technical Challenges

#### Limited Computational Resources
**Solution**: Use quantized TensorFlow Lite models, optimize preprocessing pipeline

#### Varying Lighting Conditions
**Solution**: Implement auto-exposure or use IR camera for low-light scenarios

#### Real-time Performance Requirements
**Solution**: Implement motion-triggered activation, optimize inference pipeline

### Hardware Challenges

#### Power Management
**Solution**: Implement sleep modes, optimize processing schedules

#### Weather Resistance
**Solution**: Proper enclosure selection, cable management

## Performance Metrics

### Target Specifications
- **Inference Time**: < 5 seconds per detection
- **Accuracy**: > 85% for known face recognition
- **False Positive Rate**: < 5% for unknown classification
- **Power Consumption**: < 10W average operation
- **Storage Usage**: < 2GB for model and application data

## References

1. SafeHome.org. (2025, February 11). 2025 Home Security Market Report. Retrieved from https://www.safehome.org/resources/home-security-industry-annual/, last visited: 09/28/2925

2. Howard, A. G., et al. (2017). "MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications." arXiv preprint arXiv:1704.04861. [Primary CNN Architecture Reference]

3. Schroff, F., Kalenichenko, D., & Philbin, J. (2015). "FaceNet: A unified embedding for face recognition and clustering." Proceedings of the IEEE conference on computer vision and pattern recognition.

4. Sandler, M., et al. (2018). "MobileNetV2: Inverted Residuals and Linear Bottlenecks." Proceedings of the IEEE conference on computer vision and pattern recognition.

5. TensorFlow Lite Documentation. "Deploy machine learning models on mobile and IoT devices." https://www.tensorflow.org/lite

6. Raspberry Pi Foundation. "Camera Module Documentation." https://www.raspberrypi.org/documentation/hardware/camera/

7. Parkhi, O. M., Vedaldi, A., & Zisserman, A. (2015). "Deep face recognition." British machine vision conference.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- ECE635/535 Course Professor Dr Fatima Anwar for project guidance
- TensorFlow Lite team for edge ML framework
- Raspberry Pi Foundation for hardware documentation
- Open source computer vision community
