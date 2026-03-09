# Multimodal

## Vision architecture basics

### Key Problem
Representing images: represent an image as a sequence of vectors.

### Vision Transformer (ViT)
idea: divide images into patches, flatten the patches into vectors, use a standard transformer.

## Learning image representations

### Contrastive Language-Image Pre-training (CLIP)
# idea: learn image and text representations jointly in a shared embedding space.

The representation for a paired image and its text should be close together.

The representation for an unpaired image and text should be far apart. 

loss: each term is a cross-entropy loss

usage: zero-shot
    zero-shot performance scaling as a function of pre-training compute

## Combining with a language model

### Llava

### General Pipeline
1. image preprocessing
2. image encoding
3. provide the encodings to a LLM