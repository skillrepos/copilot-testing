# Automating Testing with GitHub Copilot
## Revision 3.2 - 02/09/25

**Follow the startup instructions in the README.md file IF NOT ALREADY DONE!**

**NOTE: To copy and paste in the codespace, you may need to use keyboard commands - CTRL-C and CTRL-V.**

**Lab 1 - Using Copilot to create tests**

**Purpose: In this lab, we'll see basic ways to have Copilot create tests for us.**

1. In our repository, there is an example Python file named *prime.py* that we'll be starting with. You can open it by clicking on [**prime.py**](./prime.py) , or, in the terminal, enter

```
code prime.py
```

2. First, let's see how to use the context menu to generate some tests. Highlight the code in the *prime.py* file, right-click on it, then select *Copilot* and then *Generate Tests*. After a moment, Copilot should generate some basic tests in another temporary file to the right.

![using the context menu to gen tests](./images/new-tests-context-menu.png?raw=true "using the context menu to gen tests")

3. You can scroll down and look at the output. We're going to use the shortcut command to generate the final file we want. So, just click on the *Discard* button and then click at the top to close the proposed *test_prime.py* file. We don't need to save it.

![discard suggested tests](./images/new-discard-and-close-suggested-tests.png?raw=true "discard suggested tests")

4. Now, let's use the shortcut command */tests* to generate some tests. In the same prime.py file, highlight the code and use the *CMD+I* shortcut to bring up the inline chat dialog. In the text entry box for the dialog, enter the */tests* command and click on the arrow on the right at the end to submit it.

![using the shortcut command to gen tests](./images/new-slash-tests-command.png?raw=true "using the shortcut command to gen tests")

5. After running the command, Copilot generates some basic assert-based tests in a new file. You can just save this file as *test_prime.py*. To do this, click on the *3-bar* menu in the upper left corner of the codespace, then click *File*, then *Save As* (or use the menu shortcut). (Make sure you are saving the testing file and not the prime.py file - it will probably have a temporary name of soemthing like "import_...".) If you get a dialog asking about saving AI-generated results, just reply yes.
   
![proposed tests into new file](./images/new-slash-tests-output.png?raw=true "proposed tests into new file")
![saving file](./images/new-save-test_prime.png?raw=true "saving file")


6. We can also use comments to have Copilot create tests. Let's try this in the original *prime.py* file. Under the code, add a comment line that tells Copilot to create tests for the code above.

```
# Create tests for the code above
```

![tests from comments](./images/ct74.png?raw=true "tests from comments")

7. Hit return (if you haven't). Copilot may supply a generic testing routine, such as below, the start of a routine, or a set of actual assert-based tests (NOTE: if you only get a blank line at first, try hitting return again to see if it starts filling in the function on the second line):

```
def test_is_prime(number, expected):
    result = is_prime(number)
    assert result == expected, f"Expected {expected} but got 
{result}"
```

8. Depending on your particular comment and context, Copilot may produce a more generic testing function or a set of individual test cases. To ensure you get the latter,  delete the generated code from the previous comment and redo the steps with this comment. (You may need to hit return again and give Copilot a few seconds to generate the tests.)

```
# Create a set of 10 unit tests for the code above
```

9. In this case, Copilot will usually generate a more explicit set of tests wrapped in a testing function. An example is shown next.You can delete them after looking at them since we already have other tests.

![test by comment](./images/ct14.png?raw=true "test by comment")    

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
 
2. Let's ask Copilot for some general testing advice for this code. Switch to the separate chat area, and ask it:

```
How can I test #file:webscraper.py?
```

![query in chat](./images/new-how-to-test-select-file.png?raw=true "query in chat")

3. Copilot will likely have generated some output with a set of instruction and some example code similar to what's shown below. Notice that it brings in a unit testing framework. The generated code may not be complete - for example, it may have *placeholders* for input and output data.
   
![testing suggestions for file](./images/new-how-to-test-webscraper.png?raw=true "testing suggestions for file")

4. Let's take the generated code and put it into a new file. Click on the *Apply Edits* icon or the checkmark in the top right corner of the code block (next to the trash can).

![apply edits](./images/copilot-testing-apply-edit.jpg?raw=true "apply edits")
   
![apply edits](./images/new-click-to-apply-edits.png?raw=true "apply edits")

5. After this, you should see the testing code as a new file in your editor. **Save the file as test_webscraper.py to make sure it has the correct name.**

![insert into new file](./images/new-test-output-to-file.png?raw=true "insert into new file")

![save new file](./images/new-save-test_webscraper.png?raw=true "save new file")

6. Let's also look at how we can add code coverage information for the *webscraper.py* file. Switch to the separate chat dialog. To keep things clean, let's start a new chat. You do that by clicking on the "+" button in the upper right of the separate chat dialog. Also, *if present* remove the default context in the chat. Click on the icon next to the test_webscraper.py file to delete it as the context. (If not showing up to remove, you can click in the file and then it should show up.)

![start new chat](./images/new-new-chat.png?raw=true "start new chat")  
![delete default context](./images/new-delete-default-context.png?raw=true "delete default context")

7. Now, let's add the *webscraper.py* file as our context. In the chat input area, click on the icon that looks like a paperclip. Then in the list of options that pops up in top center, select the *webscraper.py* file. After that, it should show up in the context of the chat.

![add context](./images/new-add-context.png?raw=true "add context") 
![add context](./images/new-choose-webscraper.png?raw=true "add context") 
![updated context](./images/new-updated-context.png?raw=true "updated context") 

8. Now, let's ask Copilot how we can measure code coverage on the file? If Copilot creates a response that looks like another set of tests or testing code, then it probably ran with the */tests* shortcut. You can click on the *"rerun without"* link to get output similar to what's shown below.
```
How can I measure code coverage on this file?
```

![query on code coverage](./images/new-code-coverage.png?raw=true "query on code coverage")

9. In the chat output, you'll see a set of steps interspersed with commands that can be run from the command line. 
   
![query on code coverage](./images/new-hover-and-insert-into-terminal.png?raw=true "query on code coverage")

10. You can hover over each and click the icon that looks like a terminal to send these commands directly to the terminal. Try this with the one for "pip install coverage". When you click on that terminal icon, it should populate the terminal with that command and you can run it.
    
![insert command from chat to terminal](./images/new-command-from-chat-to-terminal.png?raw=true "insert command from chat to terminal")

11. Finally, let's have Copilot help us identify any other edge cases that we should consider. Uncheck the "eye" icon. Switch back to the *test_prime.py* file, highlight the text, and start a new chat. Then, in the Chat interface, enter the prompt "Are there any other edge cases that should be tested?". (If the test_prime.py file shows up in the context window with a mark through it, you can unclick the *eye* icon to ensure it is used.)

```
Are there any other edge cases that should be tested?
```

![finding other test cases](./images/new2-edge-cases-to-apply.png?raw=true "Finding other test cases")

12. This should result in some additional test cases being generated in Chat that you can then just replace in the *test_prime.py* file by using the *Apply in Editor* icon that shows up when you hover over the code and then clicking on the *Accept changes* link above the code change.

![adding test cases](./images/new2-apply-edge-cases.png?raw=true "Adding test cases")

    
<p align="center">
**[END OF LAB]**
</p>
</br></br>


**Lab 3 - Using other Copilot features to help with testing**

**Purpose: In this lab, we'll see how to leverage some of Copilot's other features to help with testing**

1. Let's see how the Copilot Fix functionality can help us out. Click on/open the *test_prime.py* file from the earlier labs. At the top, let's change the first line from *import unittest* to *import pytest* as if we wanted to use the other framework.
```
import pytest
```

2. Since the rest of the file is expecting *unittest* as the framework, we have some problems now in the file. In fact, if you look at the **PROBLEMS** tab at the bottom of the codespace, you can see that it flags two instances in the file where *unittest* is undefined.

![new problems](./images/new-problems-in-test_prime.png?raw=true "new problems")

3. We know what the fix is, but let's see if Copilot can help identify and correct the issue for us. Select/highlight all the code
   
![copilot fix](./images/new-copilot-fix.png?raw=true "Copilot fix")

4. Copilot should recognize that this is the wrong import and then suggest a correction/fix that you can then *Accept* from the dialog. After Accepting, you should see the set of problems for that file disappear from the PROBLEMS tab.

![copilot fix](./images/new-copilot-fix-to-accept.png?raw=true "Copilot fix")


5. Next, let's try out the Copilot */tests* shortcut command with a different kind of file and language. There's a large demo file of SQL statements in this project named [**create-tables.sql**](./create-tables.sql). Open that.

```
code create-tables.sql
```
![new file and chat](./images/new-open-create-tables-and-new-chat.png?raw=true "new file and chat")

5. Since we already have our desired file selected, we can just run the */tests* command in the chat interface. 

```
/tests 
```
![testing for SQL](./images/new-run-tests-for-sql.png?raw=true "testing for sql")   

6. After a few moments, Copilot should respond with a plan and suggested examples of how to do the steps. The interesting part is the plan and then the code that follows that.  You can just review these to see the example, you don't need to do anything with them.

![testing suggestions for SQL](./images/new-generated-plan-to-test-sql.png?raw=true "testing suggestions for sql")   

7. Suppose we need to better understand the code we're testing. We can have Copilot explain the code to us. Switch back to the *webscraper.py* file. Highlight all of the code in the file and then use the CMD/CTRL+I shortcut to bring up the chat dialog window and type in */explain*.

![explain webscraper.py](./images/ct51.png?raw=true "explain webscraper.py")   

8. This will dump a lot of output in the dialog. To better review it, click on the *View in Chat* button to put it in the main Chat interface.

![view in chat](./images/new-view-in-chat.png?raw=true "view in chat")   

9. While we're at it, let's have Copilot explain how the testing file it created for us works. Start a *new* chat. In the chat interface - enter *@workspace /explain #* and pause. There should then be a popup, where you can use the arrow key to arrow down and select the *#file* entry and hit Enter. 

```
@workspace /explain #
```

![selecting file](./images/ct54.png?raw=true "selecting file")

10. After you selecting the *#file* selector, you should get a popup near the center top of the codespace interface. This will let you select the *test_webscraper.py* file. Select that file.

![selecting file](./images/ct55.png?raw=true "selecting file")

11. You'll then have a highlighted command to explain the file. Hit Enter for that. You may or may not then have another popup to select the range of the testing file to explain. But if you do, you can just select the *TestWebScraper* entry.
 
 ![full entry](./images/ct57.png?raw=true "full entry")
 
 ![full entry](./images/ct56.png?raw=true "full entry")  

12. After executing this, you'll likely see lots of output, including example usage, code improvements, etc. But you can scan back up through the output to see the sections with explanations.

 ![explanation](./images/new-web-scraper-test-explanation.png?raw=true "explanation") 

<p align="center">
**[END OF LAB]**
</p>
</br></br>


**Lab 4 - Documentation for Testing**

**Purpose: In this lab, we'll see how to use Copilot to help document content for testing.**

1. To have the testing code be able to be maintained, it should be documented well. We can have Copilot do this for us too. In the editor, switch to the *test_webscraper.py* file and highlight the code. Open the shortcut dialog with CTRL/CMD+I and enter the */doc* command in it. 

```
/doc
```

2. Hit Enter and you'll see some documentation suggested at the start of the file. You can just go ahead and accept that.
 
 ![initial doc suggestion](./images/new-doc-test_webscraper.png?raw=true "initial doc suggestion")

3. This is useful, but we'd like to have the test cases more thoroughly documented. With the code still highlighted, bring up the chat dialog again with the CTRL/CMD+I sequence and tell Copilot in the dialog to "verbosely comment all the code so it's easy to understand".

```
verbosely comment all the code so it's easy to understand
```

![verbose doc prompt](./images/new-verbosely-comment-code.png?raw=true "verbose doc prompt")

4. Hit Enter and you should see more thorough comments suggested throughout the code body. You can go ahead and *Accept* them. (You may need to do multiple *Accepts*.)

![verbose doc suggestions](./images/new-code-with-verbose-comments.png?raw=true "verbose doc suggestions")


5. While we're working with documentation, sometimes it can be useful to have documentation on features like APIs to go off of. Let's have Copilot try to generate that for us. In the chat interface, you can just clear the current content and enter "Create API documentation for the APIs in #file:webscraper.py". After hitting Enter, you should see documentation for the APIs as requested.

```
/clear
create API documentation for the APIs in #file:webscraper.py
```

![api doc](./images/new-api-docs.png?raw=true "api doc")


6. Let's try one more doc step here. Let's have Copilot generate functional documentation to help us understand the code we're testing. Start a new chat. In the new chat interface, enter in the prompt "Create functional documentation for the #file:webscraper.py" and hit Enter. Copilot should then generate extensive documentation with the details of the file.

```
create functional documentation for the #file:webscraper.py
```

![functional doc](./images/new-functional-doc-output.png?raw=true "functional doc")


7. Having this documentation generated in Copilot is useful, but to make it more widely sharable we need to be able to save it separately. Simply copying it from the Chat interface won't preserve any generated code. To ensure you get everything, it works best to click on the "..." menu in the upper right of the Chat section and select "Open Chat in Editor". Go ahead and do that now.

![open chat in editor](./images/new-open-chat-in-editor.png?raw=true "open chat in editor")


9. In the copy of the chat that is open in the editor now, you can right-click and select *Copy All*. This will copy all the content. 

![copy markdown](./images/new-copy-chat-content-in-editor.png?raw=true "copy markdown")


10. You can then paste this into a text file, save it as .md (markdown) format and then view it in a markdown viewer or convert it.

![copy markdown](./images/ct69.png?raw=true "copy markdown")

<p align="center">
**[END OF LAB]**
</p>
</br></br>

**Lab 5 - Validating Inputs**

**Purpose: In this lab, we'll see how to have Copilot help validate inputs in functions.**

1. Copilot can also help with other kinds of validation besides general test cases. It can also validate that inputs going into a function are valid. Go back to the *prime.py* file, highlight your *is_prime* code and enter the prompt below into the Copilot Chat interface.

```
generate asserts to ensure that the inputs to the function are valid
```

2. Click on the "rerun without" link next to the "Workspace" section to get a run more targeted towards what we want.

![rerun without](./images/new-rerun-without.png?raw=true "rerun without")

3. From here, Copilot should respond and suggest asserts, as requested, to validate the functions inputs. The response may look something like the following (again you do not have to change anything).

![validating inputs with asserts](./images/new-inputs-asserts.png?raw=true "validating inputs with asserts")   

4. We can also be more directive and tell Copilot to generate checks within our *is_prime* function for valid inputs. Try this prompt (again in the Chat interface):

```
generate checks inline with the is_prime function to ensure that the inputs to the is_prime function are valid and raise an error if they are not
```

5. This should allow Copilot to generate code to validate the inputs, but with a more standard coding mechanism to surface any issues. Here's what example output from that might look like.

![validating inputs with checks](./images/new-generate-checks-to-ensure-that-inputs-to-function-are-valid.png?raw=true "validating inputs with checks")  


6. When you're happy with this code, you can go ahead and replace the highlighted code in the file by hovering over the code in the chat, clicking the apply button and then accepting the change in the file itself (click on *Accept Changes* above the updated code). 

![validating inputs with checks](./images/new-update-is-prime-with-checks-and-accept.png?raw=true "validating inputs with checks")  

7. While we are discussing inputs, we should also consider other types of inputs to test for. Switch back to the *test_prime.py* file with the test cases and have it open in the editor. Before we prompt Copilot about additional test cases, we need to be sure that it is considering the whole file for context. Even though it shows *test-prime.py* as the current file context in the chat, it will only include the part of the file that's visible in the editor.  To see that, enter this prompt and note what reference it used.

```
What other kinds of test cases should we check for?
```

8. Notice that in my example, only lines 11-28 were used as a reference - which corresponds to what was visible in the editor (aka #editor). With only a subset of the test cases visible, it's possible/likely that Copilot would repeat some that were already in the parts of the file that weren't visible in the editor.  With this prompt, Copilot will likely add some additional test cases like these.

![only visible context](./images/new-only-editor-visible-context.png?raw=true "only visible context") 
   
9. To make sure we get the entire file as context, we can follow the same process as in the previous lab. First, let's *cancel* the current context in the chat dialog by clicking on the icon that looks like an "eye" at the end of the *test-prime.py* item n the chat. (See below for where to click and what it should look like after.)
   
![disable current file context](./images/new-disable-current-file-context.png?raw=true "disable current file context") 

![disabled current file context](./images/new-disabled-current-file-context.png?raw=true "disabled current file context") 

10. Click on the *paper clip* icon and select the *test-prime.py* file from the dialog that pops up to add the entire file as context. Afterwards, the chat window should look like the second screenshot below.

![attach file context](./images/new-attach-context.png?raw=true "attach file context") 

![attached file context](./images/new-attached-file-for-context.png?raw=true "attached file context") 


11. Now, we can input the same prompt again and we should see that the entire file was used instead of just the visible portion. Input the same prompt and notice the output. Since the entire file was used as context, the new test cases should not overlap the existing ones. Afterwards, you can add the changes into the *test-prime.py* file if you want.

```
What other kinds of test cases should we check for?
```

![distinct test case context](./images/new-distinct-test-case-context.png?raw=true "distinct test case context") 

12. Finally, let's see if Copilot can help refactor our code to make it more testable. We'll use the *webscraper.py* file for this since it is more substantial.  Enter the query below in the Chat interface. 

```
refactor the code in #file:webscraper.py to make it more easily testable
```

13. You should see some suggestions for improving testability in the file in the chat output. These can be applied to the current code if you want.
    
![Refactoring for testing](./images/new-refactor-for-testability.png?raw=true "refactoring for testing")  


<p align="center">
**[END OF LAB]**
</p>
</br></br>

**Lab 6 - Leveraging frameworks and TDD**

**Purpose: In this lab, we'll see how to leverage Copilot with testing frameworks and how to do Test-Driven Development with it.**

**Important Note: If any steps in this lab run with /tests by default, run them again using the "run without" option**

1. Let's look at a TDD approach of creating the test cases with a failing test and then immplementing the code to be tested. Consider a simple example where we want to create a test class and tests for students at a university. We'll use Mockito in our testing framework. Let's have Copilot create a pom.xml file for us with a mockito dependency. In the separate chat interface, start a new chat session, and enter the following prompt:

```
add a pom.xml file with a mockito dependency version 3.3.3, and compiler source and target version 1.8
```

![add pom with mockito dependency](./images/ct33.png?raw=true "add pom with mockito dependency")  

2. Now, let's put the generated content into a new file in our project. Hover over the generated code, select the *... (More actions)* at the end and then click on *Insert into New File*. Then save the file as *pom.xml* via the *3 bar* menu in the upper left, then *File*, then *Save As..* (or use the keyboard shortcut).

![insert into new file](./images/ct34.png?raw=true "insert into new file")  

![save file](./images/ct29.png?raw=true "save file") 

3. Now, let's create an appropriate test class and initial set of tests. Do this in the Copilot separate Chat interface, since we expect a significant amount of output and we may want to put it in a separate file. We'll use a prompt that tells Copilot to focus on the *pom.xml* file we just created.

```
Referencing #file:pom.xml, create a StudentTest class for students enrolled at a university and add tests
```

4. The suggested StudentTest class from this prompt is likely overkill for what we want for a simple test case for a *Student* class. However, Copilot will likely detect that we need the Junit dependency at the start of the output. There may be a step or segment of code to *update pom.xml with JUnit dependencies* at the top or bottom of the output. (If you don't see it, click on the "Run without" to run the prompt without /tests.)  If you see it, go ahead and add that part only into your *pom.xml* file. (You can just have the **corresponding section** of the pom.xml file contents highlighted and then *Apply* to replace it.) Save the changes to the *pom.xml* file afterwards.

![add junit dependency](./images/new-update-pom-2.png?raw=true "add junit dependency")  
   
5. Let's restructure the prompt to ask for something more specific for the StudentTest class. Enter the following in chat.

```
Referencing #file:pom.xml, create only a StudentTest class for a student enrolled at a university. A student will have personal attributes such as a first and last name, a phone number, an address, and a contact email. The StudentTest class should be part of a com.example package.
```
![more specific query to create tests](./images/ct21.png?raw=true "more specific query to create tests")  

6. The output from Copilot now likely looks more like what we wanted as a starting point. Click into the output for the *StudentTest* class, hover over the top right, and use the icon (or copy and paste) to put it in a different file. Save the file as **src/test/java/com/example/StudentTest.java**.

![save new test](./images/new-save-into-file-studenttest.png?raw=true "save new test")
![save new test](./images/new-save-into-file-path.png?raw=true "save new test")

7. Now, let's execute Maven to try the testing. (Note: We expect it to fail because we don't have the *Student* class implemented yet.)

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

10. Finally, let's run the test again and it should pass. 

```
mvn test
```

![run test and see it pass](./images/ct37.png?raw=true "run test and see it pass")


<p align="center">
[END OF LAB]
</p>

<p align="center">
THANKS!
</p>
 

