# TwinCAT 3 Function Block User Guide

## Introduction

Welcome to the user guide for the TwinCAT 3 Function Blocks. This guide provides an overview of the available function blocks and their usage.

## Function Blocks Overview

### FB_Testsuites

- Manages multiple test suites.
- Adds, executes, and manages test suites.
- Provides methods for starting and stopping test suites.

### FB_Testsuite

- Represents a single test suite.
- Defines test cases and assertions.
- Handles file operations and assertion checks.

### FB_File

- Provides file manipulation functionalities.
- Creates, deletes, appends, and loads files.

### FB_ListSTRING

- Represents a list of strings.
- Adds, inserts, retrieves, and clears string items.

### FB_StringBuilder

- Builds and manipulates strings efficiently.
- Appends values and converts to string.

### FB_Assert

- Provides assertion functionalities for testing.
- Verifies conditions and checks for equality.

## Usage

1. Instantiate the desired function block.
2. Set properties and configure methods.
3. Execute methods to perform operations.
4. Check results using assertions.

## Example

### Creating a Test Suite

```ST
// Instantiate FB_Testsuite
fbTestsuite: FB_Testsuite;

// Define test cases
fbTestsuite.M_Testcase("TestName", T#1S, "", "", 1);
