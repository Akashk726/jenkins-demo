# Jenkins CI/CD Demo

## Overview
Simple Node.js app with Jenkins pipeline using SSH.

## Structure
- `Jenkinsfile`: Pipeline definition
- `Dockerfile`: Container setup
- `index.js`: App code
- `test.js`: Test script

## Running Locally
1. `npm install`
2. `npm start`

## Jenkins Setup
- Uses SSH for Git
- Pipeline: Checkout → Build → Test → Deploy
