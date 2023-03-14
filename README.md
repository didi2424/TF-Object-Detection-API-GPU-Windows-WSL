# HOW to Custom Object Detection Using Tensorflow 2.11 (GPU) with Custom Training Dataset and Custom Models inside WINDOWS WSL, Conda Environment and Nvidia GPU


<!-- The Basics -->
## The Basics

This repository is a tutorial for how to use Tensorflow's Object Detection API (boxes Classsifier) to train an image into object detection classifier on Windows 11 Host. also when Tensorflow 2.11 is not support GPU inside Windows anymore, so we can use Ubuntu on Windows as our main host 


This README.md describes every step required to get going with your custom object detection classifier :

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#the-basics">The Basics</a>
    </li>
    <li>
    <a href="#about-the-project">About The Project</a>
    <ul>
        <a href="#build-with"> Build With </a>
    </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

The purpose of this tutorial is to explain how to train you custom Convolutional Neural Network Object Detection Classifier with your custom image and Models that Tensorflow Provide, Also in this tutorial you will use a powerfull 'Jupyter Notebook' for interface and connect to your 'Ubuntu On Windows' At the end of this tutorial, you will have a program that can identify object with draw boxes aroudn specific objects in pictures, videos, or in the webcam feed.

Here's why:
* Your time should be focused on creating something amazing. A project that solves a problem and helps others
* You shouldn't be doing the same tasks over and over like creating a README from scratch
* You should implement DRY principles to the rest of your life :smile:

Of course, no one template will serve all projects since your needs may be different. So I'll be adding more in the near future. You may also suggest changes by forking this repo and creating a pull request or opening an issue. Thanks to all the people have contributed to expanding this template!

Use the `BLANK_README.md` to get started.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

This section should list any major frameworks/libraries used to bootstrap your project. Leave any add-ons/plugins for the acknowledgements section. Here are a few examples.

* [![Python][Next.js]][Next-url]
* [![React][React.js]][React-url]
* [![Vue][Vue.js]][Vue-url]
* [![Angular][Angular.io]][Angular-url]
* [![Svelte][Svelte.dev]][Svelte-url]
* [![Laravel][Laravel.com]][Laravel-url]
* [![Bootstrap][Bootstrap.com]][Bootstrap-url]
* [![JQuery][JQuery.com]][JQuery-url]


<!-- GETTING STARTED -->
## Getting Started

Tensorflow's GPU allows your PC to use the graphic card to provide extra processing power while training the dataset and the models, so it will be used for this tutoral, in the air GPU provide faster training dataset than CPU. Nowday Tensorflow => 2.11 is not supporting Windows to use a GPU. So, you are need 'Ubuntu on Windows' to solve this.

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
* npm
  ```sh
  npm install npm@latest -g
  ```

### Installation