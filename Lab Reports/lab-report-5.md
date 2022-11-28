# Lab Report 5 - Autograder

## grade.sh

<code>
    # Create your grading script here

    GRADE=0
    PERCENTAGE=0

    rm -rf student-submission
    git clone $1 student-submission

    # Check if repo cloned successfully.
    if test -d ./student-submission
    then
        echo "  Cloning Finished."
        echo "  "
    else
        echo "  Could not Clone Repo."
        echo "  "
    fi

    cp TestListExamples.java student-submission
    cp -r lib student-submission

    cd student-submission

    # Check if the file exists.
    if test -e ListExamples.java
    then
        echo "  File Found. (+1 Point!)"
        ((GRADE++))
        echo "  "
    else
        echo "  ListExamples.java not found."
        echo "  "
        PERCENTAGE=$(($GRADE * 100 / 3))
        echo "  Final Grade: [$GRADE/3] $PERCENTAGE%"
        exit 1
    fi

    # Compile and Run
    if javac -cp .:./lib/hamcrest-core-1.3.jar:./lib/junit-4.13.2.jar *.java 2> compile-err.txt
    then
        echo "  Compiled. (+1 Point!)"
        ((GRADE++))
        echo "  "
        if java -cp .:./lib/hamcrest-core-1.3.jar:./lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > test.txt
        then
            echo "  All tests were successful. (+1 Point!)"
            ((GRADE++))
            PERCENTAGE=$(($GRADE * 100 / 3))
            echo "  "
            echo "  Feedback Report:"
            echo "  ----------------"
            cat test.txt
            echo "  "
            echo "  Final Grade: [$GRADE/3] $PERCENTAGE%"
        else
            echo "  Some or all of the tests were not successful."
            PERCENTAGE=$(($GRADE * 100 / 3))
            echo "  "
            echo "  Feedback Report:"
            echo "  ----------------"
            cat test.txt
            echo "  "
            echo "  Final Grade: [$GRADE/3] $PERCENTAGE%"
        fi
    else
        echo "  Compile Error."
        echo "  "
        echo "  Feedback Report:"
        echo "  ----------------"
        cat compile-err.txt
        PERCENTAGE=$(($GRADE * 100 / 3))
        echo "  "
        echo "  Final Grade: [$GRADE/3] $PERCENTAGE%"
    fi
</code>

---

## Examples

### Incorect Implementation - Should compile successfully but not pass all the tests.
![image](../Screenshots/Lab%20Report%205/lab5-screenshot-1.png)

### Correct Implementation - Should receive full or near-full credit.
![image](../Screenshots/Lab%20Report%205/lab5-screenshot-2.png)

### Syntax Error - Should result in a compile error.
![image](../Screenshots/Lab%20Report%205/lab5-screenshot-3.png)

---

## Tracing - Correct Implementation

First, our script initializes 2 variables: <code>GRADE</code> and <code>PERCENTAGE</code>, which will be used to calculate the final score that the student received. <code>rm -rf student-submission</code> will remove the already existing submission and the script will download the new submission with <code>git clone $1 student-submission</code>, where <code>$1</code> is the repository link inputted when calling the script. For the first if statement, we check whether the repository cloned successfully. In this case, it did and that's why the script ran lines 12-13, where we outptutted "Cloning finished". If cloning failed, then we wouldn't have had a directory named <code>student-submission</code> since we delete the old one, so instead we would've outputted "Could not clone repo.". We then copied the lib folder and TestListExamples.java file into the cloned repository with <code>cp TestListExamples.java student-submission</code> and <code>cp -r lib student-submission</code> (lines 19-20). We then change the directory and enter <code>/student-submission</code>, and check whether the file exists or no (lines 25-36). In this case it does, so we output a message and increment <code>GRADE</code>. Otherwise, we wouldn't have incremented <code>GRADE</code> and we would've ended the script there since we set our exit code to 1, which will prevent the next command from executing. Line 39 checks whether the submitted code compiles or no. If it doesn't, the standard error will be redirected into a newly created file called <code>compile-err.txt</code>, and the script will output some feedback to the student including <code>compile-err.txt</code> and the final grade with the percentage and the script would've terminated there (line 65). However, in this submission, the program was compiled successfully and in fact passed all the tests, so our script skips the part where it outputs the standard error of the compilation, and increments <code>GRADE</code>. It then checks to see if the submission passed all the tests or no and saves the standard output in a file called <code>test.txt</code> (line 44). Like mentioned above, in this submission all the tests were passed, so again we increment <code>GRADE</code> for that, calculate the percentage and output what's written in <code>test.txt</code> as feedback, along with the final score. We do the same even if only some tests passed, however we don't add a point to <code>GRADE</code> since not all methods worked.

![image](../Screenshots/Lab%20Report%205/lab5-screenshot-4.png)

![image](../Screenshots/Lab%20Report%205/lab5-screenshot-5.png)