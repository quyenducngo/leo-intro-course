2. Create A New Token Project

Create the Project

To create a new project, we use the command leo new <project_name>.

	1.	Navigate to the Root Folder:
	•	Ensure you are in the root folder of this LEO-INTRO-COURSE repository when creating a new project. (You must include your code in the repository for it to be considered finished.)
	2.	Create a New Token Project:
	•	In this example, we will create a new token project with a random name:
 leo new token_$RANDOM

	•	Alternatively, you can create the token project with a custom name:
 leo new token_custom_name

	•	Note: Make sure the project name is in lower case!
 leo new token_custom_name

 
 Commands to Run and Test the Project

	1.	Enter the Project Directory:
	•	After creating the project, navigate to the project directory:
 cd token_<your_project_name>

 	2.	Build and Run the Program:
	•	To build and run the program in main.leo, use the following command:
 leo run main 0u32 1u32 # build, setup, prove, and verify

 	2.	
	•	Expected Output:
Leo ✅ Compiled 'helloworld.aleo' into Aleo instructions
⛓  Constraints
 • 'helloworld.aleo/main' - 33 constraints (called 1 time)
➡️  Output
 • 1u32
 
	•	You should see the output equal to 1u32.

For more details about Aleo project interactions, check out this guide.

Project Folder Outline

Here is an outline of the project folder structure:
<img width="886" alt="Screenshot 2024-06-02 at 1 23 51 PM" src="https://github.com/quyenducngo/leo-intro-course/assets/27698009/331c74ef-6e77-4dc1-8ff9-815cfc38dfa7">
s
