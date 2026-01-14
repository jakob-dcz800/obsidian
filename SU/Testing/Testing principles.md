---
tags:
  - Testing
  - Software-development
---
# Testing principles

## List of testing methods
[[#Ad hoc Exploratory Testing (Error Guessing)]]
[[#Regression and back-to-back testing]]
[[#Performance Testing]]
[[#Limit Testing]]
[[#Stress or Smoke Testing]]
[[#Random Testing for Property-based Testing]]
[[#Metrics]]
[[#Security Testing]]
[[#Usability Testing]]
[[#Recovery Testing]]
[[#Configuration Testing]]
[[#Compatibility Testing]]
[[#User Documentation Testing]]
[[#Validation Testing]]
[[#Customer Acceptance Testing]]
## Ad hoc Exploratory Testing (Error Guessing)

Based on intuition, guess what kinds of inputs might cause the program to fail.
Create some test cases based on your guesses.
Intuition will often lead you toward boundary cases, but not always.
Some special cases aren't boundary values, but are mishandled by many programs.
- Try exiting the program while it's still starting up 
- Try loading a corrupted file
- Try strange but legal URLs: `hTtP://Www.bYu.EDU/`

## Regression and back-to-back testing

If you have **multiple implementations of the same functionality**, you can run test inputs through both implementations, and compare the results for **equality**.

Why would you have access to multiple implementations?
- Safety-critical systems sometimes use multiple, independent implementations of critical modules to ensure the accuracy of results
- You might use a competitor's product, or an earlier version of your own, as the second implementation
- You might write a software simulation of a new chip that serves as the specification to the hardware designers. After building the chip, you could compare the results computed by the chip hardware with the results computed by the software simulator

• Any change to a software product, even a slight one, has the potential to cause bugs anywhere in the system 
• Basically, you have to assume that anything can break at any time 
• Regression testing is done on every build to ensure that new code (including bug fixes) did not break features that used to work

• It's not feasible to re-run all prior tests on every build (especially manual tests) 
• The regression test suite **is a subset of tests that covers all product areas** and can feasibly be run automatically on every build
• The regression test suite will evolve (i.e., grow larger) over time

• In addition to having regression tests that cover all functional areas of the product, you should also have a **regression test for every bug that has been fixed** 
• Whenever a bug is discovered, if you don't already have one, design a test case that can be used later to verify that the bug has been fixed 
• After the bug is fixed, re-run the test case on each new build to ensure that the bug stays fixed

• Experience has shown that fixed bugs often get “unfixed” later 
• Why? 
	• Source control mistakes (i.e., somebody unintentionally overwrites the bug fix in the code repository) 
	• The bug fix was “fragile” (i.e., it barely worked, and some later change pushes it over the edge) 
	• The feature in which the bug was found is later redesigned and re-implemented. The original mistake is repeated, thus reintroducing the bug
## Performance Testing

**Measure** the system's performance
- Running times of various tasks:
	- Throughput: unit of work / unit of time (e.g., GB/sec)
	- Latency: unit of time (e.g., u/sec)
- Resource utilization
	- Memory usage, including memory leaks 
	- Network usage (Does it consume too much bandwidth? Does it open too many connections?)
	- Disk usage (Is the disk footprint reasonable? Does it clean up temporary files properly?) 
	- Energy consumption, emissions

### Examples
• Stress test. 
• Volume test. 
• Configuration test (hardware & software). 
• Compatibility. 
• Regression tests. 
• Security tests.
• Timing tests. 
• Environmental tests. 
• Quality tests. 
• Recovery tests. 
• Maintenance tests. 
• Documentation tests. 
• Human factors tests.
## Limit Testing

Test the system at the limits of normal use. Test every limit on the program's behavior defined in the requirements.
- Maximum number of concurrent users or connections 
- Maximum number of open files 
- Maximum request size 
- Maximum file size 
- Etc.
What happens when you go slightly beyond the specified limits? Does the system's performance degrade dramatically, or gracefully?

## Stress or Smoke Testing

Test the system under extreme conditions (i.e., beyond the limits of normal use) 
	• Create test cases that demand resources in abnormal quantity, frequency, or volume 
	• Low memory conditions 
	• Disk faults (read/write failures, full disk, file corruption, etc.) 
	• Network faults 
	• Unusually high number of requests 
	• Unusually large requests or files 
	• Unusually high data rates (what happens if the network suddenly becomes ten times faster?)
	
Even if the system doesn't need to work in such extreme conditions, stress testing is an excellent way to find bugs

• Software components already translated into code are integrated into a build. 
• A series of tests designed to expose errors that will keep the build from performing its functions are created. 
• The build is integrated with the other builds and the entire product is smoke tested daily using either top-down or bottom integration.
## Random Testing for Property-based Testing

• Randomly generate test inputs 
	• Valid or invalid 
	• Could be based on some statistical model 
• How do you tell if the test case succeeded? 
	• Where do the expected results come from? 
	• Not crashing is the goal => fuzzy testing (see security)

## Metrics

$P$ is the probability
$r$ is
$θ$ is
$k$ is the partitions
### P-measure
P-measure: probability of finding at least one failing test case.
$P_{r} =1−(1−θ)^{N}$ 
$P_{p} = 1-\prod^{k}_{i=1}(1-θ)^{n_{i}}$

$θ_{i}$ is the probability that an input from partition i will cause a failure in that partition; number of test cases drawn from that partition; $k$ number of partitions.
### E-measure
E-measure expected number of triggered failures.
$E_{r}= Nθ$
$E_{p}=\sum^{k}_{i=1}n_{i}θ_{i}$
### F-measure
F-measure: expected number of test cases required to trigger an error.

## Mathematical implications

• **Partition testing**: guaranteed to perform at least as well as random if number of test cases is proportional to size of subdomain. 
• [[#E-measure]] is same when the failure rates of all partitions are the same; better in partitions strategy if we focus on the buggy partitions; better in random strategy otherwise. 
• [[#P-measure]] better on partitions if the partitions are all the same size and we choose the same # of test cases from each partition.

## Security Testing

- Any system that manages sensitive information or performs sensitive functions may become a target for intrusion
- How feasible is it to break into the system?
- Learn the techniques used by hackers 
- Try whatever attacks you can think of 
- Hire a security expert to break into the system 
- If somebody broke in, what damage could they do? 
- If an authorized user became disgruntled, what damage could they do? 
- Use automated input fuzzing to make system go down or go into ‘bad’ state

## Usability Testing

- Is the user interface intuitive, easy to use, organized, logical? 
- Does it frustrate users? 
- Are common tasks simple to do? 
- Does it conform to platform-specific conventions? 
- Get real users to sit down and use the software to perform some tasks 
- Watch them performing the tasks, noting things that seem to give them trouble 
- Get their feedback on the user interface and any suggested improvements 
- Report bugs for any problems encountered

## Recovery Testing

- Try turning the power off or otherwise crashing the program at arbitrary points during its execution 
	- Does the program come back up correctly when you restart it? 
	- Was the program’s persistent data corrupted (files, databases, etc.)? 
	- Was the extent of user data loss within acceptable limits? 
- Can the program recover if its configuration files have been corrupted or deleted? 
- What about hardware failures? Does the system need to keep working when its hardware fails? If so, verify that it does so.

## Configuration Testing

- Test on all required hardware configurations 
	- CPU, memory, disk, graphics card, network card, etc. 
- Test on all required operating systems and versions thereof 
	- Virtualization technologies such as VMWare and Virtual PC are very helpful for this 
- Test as many Hardware/OS combinations as you can 
- Test installation programs and procedures on all relevant configurations
## Compatibility Testing

• Test to make sure the program is compatible with other programs it is supposed to work with. 
	• Example: Can Word 12.0 load files created with Word 11.0? 
	• Example: "Save As… Word, Word Perfect, PDF, HTML, Plain Text" 
	• Example: "This program is compatible with Internet Explorer and Firefox" 
• Test **all compatibility requirements**

## User Documentation Testing

• Test all instructions given in the documentation to ensure their completeness and accuracy 
• For example, “How To …” instructions are sometimes not updated to reflect changes in the user interface 
• Test user documentation on real users to ensure it is clear and complete

## Validation Testing

• Ensure that each function or performance characteristic **conforms to its specification**. 
• Deviations (deficiencies) must be negotiated with the customer to establish a means for resolving the errors. 
• Configuration review or audit is used to ensure that all elements of the software configuration have been properly developed, catalogued, and documented to allow its support during its maintenance phase.

## Customer Acceptance Testing

• After system testing is complete, the customer might perform a "customer acceptance test" before signing off on the product 
• The customer acceptance test is a suite of tests that will be run by the customer (or someone they hire) to ensure that the product meets requirements