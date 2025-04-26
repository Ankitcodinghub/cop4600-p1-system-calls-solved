# cop4600-p1-system-calls-solved
**TO GET THIS SOLUTION VISIT:** [COP4600 P1: System Calls Solved](https://www.ankitcodinghub.com/product/cop4600-p1-system-calls-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;40984&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;COP4600 P1: System Calls Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
<h1>Overview</h1>
You will implement a system call in Reptilian along with two static library functions that allow the system call to be invoked from a C API. These custom system calls will <em>get</em> and <em>set</em> a custom process table attribute you will create, called <em>security level</em>.&nbsp; We will provide a program that exercises and demonstrates the new call. You’ll then create a short video to demonstrate your code. You’ll submit the project via Canvas.

&nbsp;

<strong>NOTE: Take Snapshots in VirtualBox! You will likely brick your machine at some point during this or other projects, and you will not want to start from scratch. <u>No, seriously – take snapshots!</u> </strong>

<h1>Structure</h1>
The project is broken into four main parts:

&nbsp;

<ul>
<li>Create a custom <em>security level </em>attribute for all processes.</li>
<li>Create system calls that allows a process to <em>get</em> or <em>set</em> the <em>security level </em>of a process.</li>
<li>Create static library functions that allow the system calls to be invoked via a C API.</li>
</ul>
&nbsp;

&nbsp;

<table width="566">
<tbody>
<tr>
<td width="168">User Program</td>
<td width="29">→</td>
<td width="168">Library</td>
<td width="30">→</td>
<td width="172">System Call</td>
</tr>
</tbody>
</table>
<strong>Figure 1: A system call invoked from a user program </strong>

&nbsp;

While exact implementation may vary, the library functions must match the signatures laid out in this document, and the system calls must apply the security model properly.

&nbsp;

<h2>System Call</h2>
Each process in the modified system will have a <em>security level</em>. The rules for this system will be based on a write restricted access model, namely:

&nbsp;

<ul>
<li>All processes should be <u>initialized</u> with a <em>security level</em> of zero (0).</li>
<li>A process running as the <u>superuser</u> may read and write the <em>security level</em> of any process.</li>
<li>A user process can <u>read</u> the <em>security level</em> of any process.</li>
<li>A user process can <u>write</u> the <em>security level</em> of a process at a lower level.</li>
<li>A user process may only raise the level of a process to its own level (not above it).</li>
<li>A user process can lower its own <em>security level</em> (but not that of other processes with the same level).</li>
</ul>
&nbsp;

The <em>security level</em> of each process must be stored in the process table; as such, you will need to modify the process table to add an entry for it. They are called via <sub>syscall(call_number, param1, param2)</sub>.<em> <strong>Your system call must be limited to no more than <u>two</u> parameters!</strong></em>

&nbsp;

<h2>Static Library</h2>
You will create a static library to invoke the system calls in a directory named <strong><sub>securitylevel</sub></strong>. This will be composed of a header with name <strong><sub>securitylevel.h</sub></strong> and a static library file named <strong>libsecuritylevel.a</strong><em>.</em> You will also need to provide a Makefile for this library in the directory. All other sources must be contained within the <strong><sub>securitylevel</sub></strong> directory. Please note, <em><u>these names of these</u> <u>files must match exactly!</u></em>

&nbsp;

You will create a tarred gzip file of the <strong>securitylevel</strong> directory with name <strong>securitylevel.tar.gz</strong>. When testing your code, we will decompress the archive, enter the <strong><sub>securitylevel</sub></strong> directory, and build. All functions enumerated below must be made available by including <strong>“securitylevel.h”</strong>. See <em>Submission</em> for details.

&nbsp;

In addition to the standard library functions, you will implement testing harness functions. The testing harness functions are used to verify security of the system calls from the system library (and are required for full credit on this assignment). We will call these functions to retrieve the information needed to make a system call. We will then call the system call within our own program. This ensures that no security checks are being done in the user-level library.

<strong>Figure 2: The harness functions can be used to simulate the system calls </strong>

&nbsp;

&nbsp;

<u>Library Functions</u>

These functions are to be used by programs.

<em>&nbsp;</em><em>int</em> <strong>set_security_level</strong>(int pid, int new_level)

Invokes system call which attempts to change the process identified by <strong>pid</strong> to security level <strong>new_level</strong>. Returns <strong>new_level</strong> on success, and <strong>-1</strong> otherwise.

&nbsp;

<em>int</em> <strong>get_security_level</strong>(int pid)

Invokes system call which reads the security level of the process identified by <strong>pid</strong>. Returns the security level on success, and <strong>-1</strong> otherwise.

&nbsp;

<u>Harness Functions</u>

System call parameter retrieval data should be returned as a <u>pointer</u> to an <strong>int</strong> <u>array</u> of 2-4 values that can be used to make the system call. It has this format:

&nbsp;

{ call_number, num_parameters [, parameter1] [, parameter2] }

&nbsp;

e.g.: { 42, 2, 867, 5309 } à syscall(42, 867, 5309)

<em>&nbsp;</em>

<em>int*</em> <strong>retrieve_set_security_params</strong> (int pid, int new_level)

Returns an <strong>int</strong> array of 2-4 values that can be used to make the set-security system call.

&nbsp;

<em>int*</em> <strong>retrieve_get_security_params</strong> (int pid)

Returns an <strong>int</strong> array of 2-4 values that can be used to make the get-security system call.

&nbsp;

<em>int</em> <strong>interpret_set_security_result</strong> (int ret_value)

After making the system call, we will pass the syscall return value to this function call. It should return <strong>set_security_level</strong><sup>’s interpretation of the system call completing with return value </sup><strong>ret_value</strong>.

&nbsp;

<em>int</em> <strong>interpret_get_security_result</strong> (int ret_value)

After making the system call, we will pass the syscall return value to this function call. It should return <strong>get_security_level</strong><sup>’s interpretation of the system call completing with return value </sup><strong>ret_value</strong>.

<strong>&nbsp;</strong>

<h1>Submissions</h1>
You will submit the following at the end of this project:

&nbsp;

<ul>
<li>Report on Canvas</li>
<li>Screencast on Canvas</li>
<li>Kernel Patch File (<strong><sub>diff</sub></strong>) on Canvas</li>
<li>Compressed tar archive (<strong><sub>tar.gz</sub></strong>) for <strong>securitylevel</strong> library on Canvas</li>
</ul>
<strong>&nbsp;</strong>

<h2>Report</h2>
Your report will explain how you implemented the new system call, including what changes were made to which files and why for each.&nbsp; It will describe how testing was performed and any known bugs. The report may be in Portable Document Format (pdf) and should be no more than a page. It should cover all relevant aspects of the project and be organized and formatted professionally – <strong><em>this is not a memo!</em></strong>

&nbsp;

<h2>Screencast</h2>
In addition to the written text report, you should submit a screencast (with audio) walking through the changes you make to the operating system to enable the system calls (~5 minutes).

&nbsp;

<h2>Patch File</h2>
The patch file will include all changes to all files in a single patch. Applying the patches and remaking the necessary parts of Reptilian, then rebooting and then building the test code (which we will also copy over) should compile the test program.

&nbsp;

Your project will be tested by applying the patch by switching to <strong>/usr/rep/src/kernel</strong> and running:

<strong>&nbsp;</strong>

<strong>$</strong> <strong>git apply p1.diff</strong>

<strong>$</strong> <strong>make &amp;&amp; sudo make install &amp;&amp; sudo make modules_install</strong>

&nbsp;

<h2>Compressed Archive (securitylevel.tar.gz)</h2>
Your compressed tar file should have the following directory/file structure:

&nbsp;

securitylevel.tar.gz&nbsp; &nbsp; securitylevel.tar&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; securitylevel (directory)&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; securitylevel.h

Makefile

(Other source files)

&nbsp;

To build the library, we will execute these commands:

&nbsp;

<strong>$ </strong><strong>tar zxvf securitylevel.tar.gz</strong>

<strong>$ </strong><strong>cd securitylevel</strong>

<strong>$ </strong><strong>make</strong> <strong>$ </strong><strong>cd ..</strong><strong>&nbsp; </strong>

To link against the library, we will execute this command:

<strong>&nbsp;</strong>

<strong>$ </strong><strong>cc -o program_name sourcefile.c -L ./securitylevel -lsecuritylevel</strong>

<strong>&nbsp;</strong>

Please test your library build and linking before submission! If your library does not compile it will result in <strong><u>zero credit</u></strong> (0, none, goose-egg) for the library portion of the project.
