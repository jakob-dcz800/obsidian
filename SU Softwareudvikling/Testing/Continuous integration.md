# Continuous integration

• Some projects wait several weeks between integrations 
	• Between integrations, engineers work on their pieces in relative isolation 
	• Each integration produces a new "build" 
	• The system may not build successfully between integrations 
	
• A better approach for many projects is "continuous integration" 
	• A minimal working system is checked into source control 
	• Engineers check in new code every time they finish a meaningful unit of work 
	• Engineers must never break the build, and are responsible for adding new test cases to exercise the new code 
	• The system is built, and tests are run every night to ensure that all is well • The system is always integrated and build-able