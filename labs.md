# Automating Testing with GitHub Copilot
## Revision 4.0 - 10/01/25

**Follow the startup instructions in the README.md file IF NOT ALREADY DONE!**

**NOTE: To copy and paste in the codespace, you may need to use keyboard commands - CTRL-C and CTRL-V.**

**Lab 1 - Using Copilot to create tests**

**Purpose: In this lab, we'll see basic ways to have Copilot create tests for us.**

1. In our repository, there is an example Python file named *prime.py* that we'll be starting with. You can open it by clicking on [**prime.py**](./prime.py) , or, in the terminal, enter

```
code prime.py
```

<br><br>

2. First, let's see how to use the context menu to generate some tests. Highlight the code in the *prime.py* file, right-click on it, then select *Generate Code* and then *Generate Tests*. After a moment, Copilot should generate some basic tests in another temporary file to the right.

![using the context menu to gen tests](./images/ct93.png?raw=true "using the context menu to gen tests")

<br><br>

3. You can scroll down and look at the output. We're going to use the shortcut command to generate the final file we want. So, just click on the *Close* or *Discard* button and then click at the top to close the proposed *test_prime.py* file. We don't need to save it.

![discard suggested tests](./images/new-discard-and-close-suggested-tests.png?raw=true "discard suggested tests")

<br><br>

4. Now, let's use the shortcut command */tests* to generate some tests. In the same prime.py file, highlight the code and use the *META-KEY+I* shortcut to bring up the inline chat dialog. In the text entry box for the dialog, enter the */tests* command and click on the arrow on the right at the end to submit it.

![using the shortcut command to gen tests](./images/new-slash-tests-command.png?raw=true "using the shortcut command to gen tests")

<br><br>

5. After running the command, Copilot generates some basic assert-based tests in a new file. You can just save this file as *test_prime.py*. To do this, click on the *3-bar* menu in the upper left corner of the codespace, then click *File*, then *Save As* (or use the menu shortcut). (Make sure you are saving the testing file and not the prime.py file - it will probably have a temporary name of something like "import_...".) If you get a dialog asking about saving AI-generated results, just reply yes.
   
![proposed tests into new file](./images/new-slash-tests-output.png?raw=true "proposed tests into new file")
![saving file](./images/new-save-test_prime.png?raw=true "saving file")

<br><br>


6. Now you can run the tests that were generated. In the *TERMINAL* panel, run the command below. (The "-s" option tells pytest not to capture stdout/stderr.)

```
pytest -s test_prime.py
```
<br><br>

7. The tests should pass but you will probably see a failure. (If not, to continue with the next steps, you can add/change a line that says "assert is_prime(0) == False".)

![failed test](./images/ct132.png?raw=true "failed test")

<br><br>

8. Let's have Copilot fix the failures. If the Copilot Chat panel is not already open, then click on the Copilot icon at the top. And/or if it is  not already in Ask mode at the bottom (says "Agent" or "Edit" instead), switch to *Ask* mode  via the drop-down at the bottom. (**NOTE:** If you don't see *Ask* mode or an option to switch to another mode, you may need to complete a setup step as shown in the second screenshot below. Click on the Copilot icon in the bottom status bar and look for a button that says "*Finish setup*" and click on that. Then you should see the options.)

**Opening Chat if not open**

![Opening chat panel](./images/mcp69.png?raw=true "Opening chat panel")
<br>

**Completing setup - if needed**

![Completing setup](./images/mcp88.png?raw=true "Completing setup")
<br>

**Switching to Ask mode**

![Switching to Agent mode](./images/sdlc91.png?raw=true "Switching to Agent mode")
<br><br>


9. Now, make sure the test_prime.py file is selected so it will be the current context (or drag and drop it on the Chat input area). Then enter the prompt below and submit:

```
Update the test to pass without changing implementation. 
Mark non-positive inputs as expected failures (xfail) and keep the rest as-is.
```

![Fixing tests](./images/ct129.png?raw=true "Fixing tests")

<br><br>

10. After this completes, Copilot should generate suggested updated code with the logging and messaging in the Chat interface. Hover over the block of code and click on the left +/- icon to apply the changes to the existing file.

![Adding logging](./images/ct133.png?raw=true "Adding logging")

<br><br>

11. After applying the changes, the test_prime.py file will have the suggested updates in it for review, color-coded by change. You can review the changes, but accept/keep the changes, either by clicking on the *Keep* button at the bottom or on the checkmarks for each individual change.


![Keep changes](./images/ct134.png?raw=true "Keep changes")

<br><br>

12. Now if you run the test command again, you should see that the tests that previously failed are now marked as expected failures.

```
pytest -s test_prime.py
```

![Keep changes](./images/ct135.png?raw=true "Keep changes")


<p align="center">
**[END OF LAB]**
</p>
</br></br>


**Lab 2 - High-level Copilot Testing Advice**

**Purpose: In this lab, we’ll start to learn about getting more general assistance from Copilot for testing**

1. In our repository, there is an example Python file we'll be using to start with. You can open it by clicking on [**webscraper.py**](./webscraper.py) , or, in the terminal, enter

```
code webscraper.py
```

<br><br>

2. Now, let's ask Copilot for some general testing advice for this code. With *webscraper.py* selected in the editor, in the Chat input area, enter the following:

```
Create tests for this file.
```

![query in chat](./images/ct96.png?raw=true "query in chat")

<br><br>

3. Copilot should generate a set of code for testing in a block in the chat panel, similar to what's shown below. 
   
![testing code for file](./images/ct97.png?raw=true "testing code for file")

<br><br>

4. You can hover over the block of code in the chat panel, click on the "..." entry at the end, and then select "Insert into New File" to get the code into the editor.

![insert into new file](./images/ct98.png?raw=true "insert into new file")

<br><br>

5. After this, you should see the testing code as a new file in your editor. **Save the file as test_webscraper.py to make sure it has the correct name.** (You can use the 3-bar menu item on the upper left, then *File*, then *Save As* or you can use the keyboard shortcut.)

![save new file](./images/new-save-test_webscraper.png?raw=true "save new file")

<br><br>

6. Let's also look at how we can add code coverage information for the *webscraper.py* file. Switch to the separate chat dialog. To keep things clean, let's start a new chat. You do that by clicking on the "+" button in the upper right of the separate chat dialog. Also, *if present* remove the default context in the chat. Click on the "x" icon next to the test_webscraper.py file to delete it as the context. (If not showing up to remove, you can click in the file and then it should show up.)

![start new chat](./images/ct136.png?raw=true "start new chat")  
![delete default context](./images/ct102.png?raw=true "delete default context")

<br><br>

7. Now, let's add the *webscraper.py* file as our context. In the chat input area, click on the area with the icon that looks like a paperclip and says *Add Context...*. Then in the list of options that pops up in top center, scroll down and select the *webscraper.py* file (or type it in). After that, it should show up in the context of the chat.

![add context](./images/ct88.png?raw=true "add context") 
 
![updated context](./images/ct137.png?raw=true "updated context") 

<br><br>

8. Now, let's ask Copilot how we can measure code coverage on the file? 
```
How can I measure code coverage on this file?
```

![query on code coverage](./images/ct101.png?raw=true "query on code coverage")

<br><br>

9. In the chat output, you'll likely see a block of code for doing coverage. We want the full set of commands that we also need to run. If you don't see individual steps interspersed with commands that can be run from the command line, click on the *(rerun without)* link above the output. Then you should see the commands also.
   
![rerun without](./images/ct138.png?raw=true "rerun without")

![query on code coverage](./images/ct100.png?raw=true "query on code coverage")


<br><br>

10. Hover over one of the commands. You may see an icon that looks like a terminal (first screenshot below). If you do, click on that to send the command directly to the terminal. If you don't see that icon, hover and click on the "..." option. Then select "Insert into terminal" (second screenshot below). These operations should populate the terminal with that command and you can run it.
    
![insert command from chat to terminal](./images/new-command-from-chat-to-terminal.png?raw=true "insert command from chat to terminal")

![insert command from chat to terminal](./images/ct139.png?raw=true "insert command from chat to terminal")

<br><br>

11. Finally, let's have Copilot help us identify any other edge cases that we should consider. Click on the "x" icon in *webscraper.py* to remove it from the context. Switch back to the *test_prime.py* file, highlight the text, and start a new chat. Then, in the Chat interface, enter the prompt "Are there any other edge cases that should be tested?". (If the test_prime.py file shows up in the context window with a "+" next to it, you can click on the "+"* icon to ensure it is used.)

```
Generate code for any other edge cases that should be tested.
```

![finding other test cases](./images/ct143.png?raw=true "Finding other test cases")

<br><br>

12. This should result in some additional test cases being generated in Chat that you can then just include in the *test_prime.py* file by using the *Apply in Editor* icon that shows up when you hover over the code.  Then in the updated file, you can click on the *Keep* link above the code change.

![adding test cases](./images/ct142.png?raw=true "Adding test cases")

    
<p align="center">
**[END OF LAB]**
</p>
</br></br>


**Lab 3 - Using other Copilot features to help with testing**

**Purpose: In this lab, we'll see how to leverage some of Copilot's Agent Mode to help with testing**

1. Let's see how Copilot's Agent Mode can help us out. Start a new chat by clicking on the "+" sign in the upper right of the chat panel. Then, in the chat input area, click on the down arrow next to *Ask* and select *Agent*.

![new chat and mode](./images/ct144.png?raw=true "new chat and mode")


2. Let's look at testing with a different kind of file and language. There's a large demo file of SQL statements in this project named [**create-tables.sql**](./create-tables.sql). Open that.

```
code create-tables.sql
```
![new file and chat](./images/new-open-create-tables-and-new-chat.png?raw=true "new file and chat")


3. In the chat area, with *Agent* selected, enter the following prompt to have Copilot run our tests for us. (The *create-tables.sql* file should already be set as the context since we just opened it. Tell Copilot's agent to test the sql code with the following prompt.

```
test create-tables
```

4. After you submit this, the agent will search for existing test files. Since we don't have any, it will ask if we want it to generate one. Respond in the chat with something like the following:

```
Yes, generate a Python test file to validate the SQL table creation.
```

![new file and chat](./images/ct145.png?raw=true "new file and chat")

5. After a moment, Copilot will create a test file and then ask if it can run it. You can click the *Allow* button to let it continue. (You can also click the down arrow next to *Allow* and select an option from there if there are others like *Always allow for this workspace*.)

![Allow](./images/ct146.png?raw=true "Allow")

6. If tests fail, Copilot may suggest some adaptations to change the script or the tests. If it stops generating output and asks a question, you can just respond in the chat with something like:

```
Yes, continue
```

![continue](./images/ct148.png?raw=true "continue")


7. If it pauses and asks about running commands, you can just click *Allow* or click the down arrow next to *Allow* and select *Enable Auto Approve...* and then *Allow*.

![Allow](./images/ct149.png?raw=true "Allow")

8. Allow the agent to continue with the process until the tests pass successfully. Once that happens, you can review the suggested changes/new files if you want. Then click on the *Keep* button in the section above the chat.

![Allow](./images/ct150.png?raw=true "Allow")

9. Suppose we need to better understand how the generated testing code works. We can have Copilot explain that to us. Highlight all of the code in the *test_create_tables.py* file (or whatever the test file was named) and then use the CMD/CTRL+I shortcut to bring up the chat dialog window type in */explain*.

![explain test file](./images/ct151.png?raw=true "explain test file")   

10. This will dump a lot of output in the dialog. To better review it, click on the *View in Chat* button to put it in the main Chat interface.

![view in chat](./images/ct152.png?raw=true "view in chat")   


<p align="center">
**[END OF LAB]**
</p>
</br></br>


**Lab 4 - Editing with Copilot**

**Purpose: In this lab, we'll see how to use Copilot Edit to update our tests.**

1. First, switch in the chat interface to *Edit* mode via the dropdown next to *Agent*.

![switch to edit](./images/ct153.png?raw=true "switch to edit")   

<br><br>

2. Next, let's add all of our *test_<name>.py* files as context. You can do this by dragging them from the file list to the chat input section or you can click on the *Add Context* button and select them from the drop-down list.

![set context](./images/ct157.png?raw=true "set context")   

![set context](./images/ct154.png?raw=true "set context")   

<br><br>

3. With the files selected for editing, we'll provide direction to Copilot on how to update them. Let's focus on providing good documentation and logging. In the chat area, enter the following prompt:

```
Verbosely comment all test cases and add logging
```

![edit prompt](./images/ct155.png?raw=true "edit prompt") 

<br><br>

4. As Copilot works on the changes, you'll see the files from the context being updated in the chat area.


![edits in progress](./images/ct156.png?raw=true "edits in progress")

<br><br>

5. When the changes are done, you can review them and then click the global *Keep* button in the section above the chat (or click *Keep* on the individual changes) to persist the updates.

![edits in progress](./images/ct158.png?raw=true "edits in progress")

<br><br>


6. Let's try one more doc step here. Let's have Copilot generate functional documentation to help us understand the different test cases for each file. First make sure the same three files are added as context in the chat area as before.

<br><br>

7. Now, enter the prompt below to generate the doc.

```
In a separate markdown file for each file in context, create documentation that functionally describes each test case.
```

![functional doc](./images/ct159.png?raw=true "functional doc")

<br><br>

8. As before, Copilot will process the query for each file in turn, creating a corresponding .md file.


![functional doc creation](./images/ct160.png?raw=true "functional doc creation")


<br><br>

9. When it's done, you can look at each .md file in the editor to see the results.

![viewing results](./images/ct161.png?raw=true "viewing results")

<br><br>

10. After looking at the results, you can click on the *Keep* button(s) to persist the changes.


<p align="center">
**[END OF LAB]**
</p>
</br></br>

**Lab 5 - Connecting Applications to MCP Servers**

**Purpose: In this lab, we'll see how to connect GitHub Copilot to the GitHub MCP Server.**

1. For authentication to GitHub, we will need a GitHub personal access token (PAT). When logged into GitHub, click on the link below, provide a note and click the green "Generate token" button at the bottom.

Link:  Generate classic personal access token (repo & workflow scopes) https://github.com/settings/tokens/new?scopes=repo,workflow

![Creating token](./images/mcp10.png?raw=true "Creating token")

![Creating token](./images/mcp87.png?raw=true "Creating token")

<br><br>
   
2. On the next screen, make sure to copy the generated token and save it for use later in the lab. You will not be able to see the actual token again!

![Copying token](./images/mcp11.png?raw=true "Copying token")
<br><br>

3. Now we need to add the GitHub MCP Server configuration in our IDE. You could fill most of this out via IDE prompts, but for simplicity, we already have a sample configuration file that we can just copy in. Run the commands below in the terminal. The last one will open the file in the editor.

```
cd /workspaces/copilot-testing
mkdir .vscode
cp extra/mcp_github_settings.json  .vscode/mcp.json
code .vscode/mcp.json
```

<br><br>

4. Next, we can start the local MCP server. In the *mcp.json* file, above the name of the server, click on the small *Start* link (see figure below). A dialog will pop up for you to paste in your PAT. Paste the token in there and hit *Enter*. (Note that the token will be masked out.)

![Starting the server](./images/mcp23.png?raw=true "Starting the server")

After this, you should see the text above the server name change to "√Running | Stop | Restart | ## tools | More...".

![Starting the server](./images/mcp24.png?raw=true "Starting the server")

<br><br>

5. To see the tools that are available, in the Copilot Chat dialog, make sure are in *Agent* mode, click on the small *tool* icon (see figure) and then scroll down to the *MCP Server: GitHub MCP Server* section. You'll see the available tools we picked up under that.

![Viewing available tools](./images/mcp25.png?raw=true "Viewing available tools")

<br><br>


6. Now that we have these tools available, we can use them in Copilot's Chat interface. (Again, you must be in *Agent* mode.) Here an example prompt to list out open issues in the GitHub repository the codespace is based on:

```
What are 
Give me a list of the open issues for the current GitHub repo
```
</br></br>

7. Notice the mention of "Ran <tool name> - GitHub MCP Server (MCP Server) early in the output.

![Example usage](./images/ct162.png?raw=true "Example usage")

8. Now we can use the MCP tools to help answer questions in conjunction with our local changes. For example, assuming the first issue it listed was the one about "Add unit tests for existing Python modules", we can ask if our local changes resolve this. Try this prompt in the chat area.

```
Is the first issue in the GitHub repository already solved by my local code?
```

9. After you run this, Copilot will likely tell you that yes, the issue is resolved by your local changes. (If you need to *Allow/Approve* operations from the agent to complete this, go ahead.)

![Example usage](./images/ct163.png?raw=true "Example usage")

10. If you click on the *Extensions* icon on the left (#1 in the screenshot below), you'll see a category for *MCP SERVERS - INSTALLED*. This should show the GitHub MCP Server since we just connected to that.   

![Extensions and browser](./images/mcp97.png?raw=true "Extensions and browser")

11. If you then click on the globe icon (#2 in the screenshot above), you can get to another page that shows a list of available MCP servers to use.

![MCP Servers](./images/mcp98.png?raw=true "MCP Servers")

 <p align="center">
**[END OF LAB]**
</p>
</br></br></br>


**Lab 6 - Leveraging frameworks and TDD**

**Purpose: In this lab, we'll see how to leverage Copilot with testing frameworks and how to do Test-Driven Development with it.**

**Important Note: If any steps in this lab run with /tests by default, run them again using the "run without" option**

1. Let's look at a TDD approach of creating the test cases with a failing test and then immplementing the code to be tested. Consider a simple example where we want to create a test class and tests for students at a university. We'll use Mockito in our testing framework. Let's have Copilot create a pom.xml file for us with a mockito dependency. In the separate chat interface, start a new chat session, and enter the following prompt:

```
add a pom.xml file with a mockito dependency version 3.3.3, and compiler source and target version 1.8
```

2. You may see a button to create the file. If so, click on that and then accept the suggested default location to save it. After that, the file should be visible in an editor tab.

If you don't have a button in the chat to create the file, you can just hover over the code, click "...", then "Insert into New File" and *Save* it as */workspaces/copilot-testing/pom.xml*. 
   
![add pom with mockito dependency](./images/copilot-testing-lab6-step1a.jpg?raw=true "add pom with mockito dependency") 
   
![add pom with mockito dependency](./images/copilot-testing-insert-pom-file.png?raw=true "add pom with mockito dependency")  

3. Now, let's create an appropriate test class and initial set of tests. Do this in the Copilot separate Chat interface, since we expect a significant amount of output and we may want to put it in a separate file. We'll use a prompt that tells Copilot to focus on the *pom.xml* file we just created. 

```
Referencing #file:pom.xml, create a StudentTest class for students enrolled at a university and add tests
```

4. The suggested StudentTest class from this prompt is likely overkill for what we want for a simple test case for a *Student* class. However, Copilot will likely detect that we need the Junit dependency at the start of the output. There may be a step or segment of code to *update pom.xml with JUnit dependencies* at the top or bottom of the output. (If you don't see it, click on the "Rerun without" to run the prompt without /tests.)  If you see it, go ahead and add that part only into your *pom.xml* file. (You can just hover over the chat ouput showing pom.xml updates and then click on the *Apply in Editor* icon to have the changes suggested in the actual pom.xml file. You can then click on *Accept changes* to make the changes permanent.) Save the changes to the *pom.xml* file afterwards.

**Only if Copilot didn't flag the missing dependency, run the prompt below and it should identify it so you can apply the updates.**
```
identify any missing dependencies in pom.xml
```

![add junit dependency](./images/new-update-pom-2.png?raw=true "add junit dependency")  
   
5. Let's restructure the prompt to ask for something more specific for the StudentTest class. Enter the following in chat.

```
Referencing #file:pom.xml, create only a StudentTest class for a student enrolled at a university. A student will have personal attributes such as a first and last name, a phone number, an address, and a contact email. The StudentTest class should be part of a com.example package.
```
![more specific query to create tests](./images/ct21.png?raw=true "more specific query to create tests")  

6. The output from Copilot now likely looks more like what we wanted as a starting point. Click into the output for the *StudentTest* class, hover over the top right, and use the icon (or copy and paste) to put it in a new file. Save the file as **src/test/java/com/example/StudentTest.java**. Answer *yes* to any prompts about creating the folder.

![save new test](./images/new-save-into-file-studenttest.png?raw=true "save new test")
![save new test](./images/new-save-into-file-path.png?raw=true "save new test")

7. Now, let's execute Maven to try the testing. (Note: We expect it to fail because we don't have the *Student* class implemented yet.) Run the following command in the *TERMINAL*.

```
mvn test
```

![initial test](./images/ct32.png?raw=true "initial test")


8. Folllowing the TDD methodology, let's next create the minimum code to make this test pass. We can use Copilot for that. Make sure the *StudentTest.java* file is open in the editor, and then use this prompt to create the code.

```
Referencing #editor, create a student class with verbose comments.
```

![output of query to create student class with comments](./images/ct35.png?raw=true "output of query to create student class with comments")

9. As we did before, hover over the output, insert the code into a new file. Then save it as **src/main/java/com/example/Student.java**

![saving student file](./images/new-save-into-file-student.png?raw=true "saving student file")

10. Finally, let's run the test again and it should pass. Execute the command below in the *TERMINAL*.

```
mvn test
```

![run test and see it pass](./images/ct37.png?raw=true "run test and see it pass")

**Lab 6 (Alternate) - Using the GitHub Copilot CLI to do TDD. Only works for paid Copilot plans that are authorized to use the CLI**

**Purpose: In this lab, we'll see how to leverage the Copilot CLI to do Test-Driven Development.**

1. First, let's start the Copilot CLI. In the *TERMINAL*, start the CLI with the command below. Then you'll see an opening screen like the one in the screenshot.

```
copilot
```

![cli startup](./images/ct110.png?raw=true "cli startup")

2. We should already be logged in and since we opened Copilot in a project directory, Copilot will ask if we trust the files in the folder. We have 3 options we can choose by using the number keys or the arrow keys with Enter. Since we trust the files and want Copilot to remember that we trust the files going forward, choose option 2.

![cli confirm](./images/ct111.png?raw=true "cli confirm")

3. We'll now be at the place where we can tell Copilot what we want it to do. Let's have Copilot start the TDD process for a class that manages students at a university. We'll give it direction on which testing framework to use also. Enter the prompt below and then submit it.

```
Create a new Python project in a src directory. I want to use pytest and practice test-driven development for a Student class with name, email, phone, and address attributes.
```

![starting prompt](./images/ct113.png?raw=true "starting prompt")

4. After this, Copilot will start working through the process. When it gets to a point where it needs to execute a command in the shell, it will stop and ask if it's ok for it to run the command(s). You can just respond with #2 again to let it know it's ok to run this command this time and in the session going forward.

![run command](./images/ct114.png?raw=true "run command")

5. As Copilot continues with generating files and running commands to set things up, you can just respond and approve it to do the needed operations. (Note that sometimes it may phrase things as "Do you want" when it really means "Is Copilot allowed".)
   
![run command](./images/ct115.png?raw=true "run command")

6. As it proceeds with the process, it should install pytest and run the tests to see them fail - the "red" phase of TDD.

![red phase](./images/ct118.png?raw=true "red phase")

7. After the tests fail, you'll see it create the minimal implementation Student class to make the tests pass and then run them - the "green" phase of TDD.

![green phase](./images/ct123.png?raw=true "green phase")

8. From here, Copilot will likely add test coverage automatically.

![add coverage](./images/ct124.png?raw=true "add coverage")

9. Finally, it will add some documentation and supporting files and then share information about what it has done, including the file structure and other details.

![summary structure](./images/ct121.png?raw=true "summary structure")

![summary overall](./images/ct122.png?raw=true "summary overall")

10. Note that while Copilot did most of the work here, we had a view into what was happening at each point and approval for any operations that made changes. If you want, you can further examine the files that Copilot generated and/or run any of the available *make commands*.

<p align="center">
[END OF LAB]
</p>

<p align="center">
THANKS!
</p>
 

