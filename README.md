<div align="center">

## \_Send E\-mail\_


</div>

### Description

This is a very simple script that will send an e-mail using the standard mail () function. Designed for beginners. I was going to upload it but it didn't work so here's the code.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[BelgiumBoy\_007](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/belgiumboy-007.md)
**Level**          |Advanced
**User Rating**    |4.4 (44 globes from 10 users)
**Compatibility**  |PHP 4\.0
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__8-1.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/belgiumboy-007-send-e-mail__8-1421/archive/master.zip)





### Source Code

<code><font color="#000000">
<font color="#0000BB">&lt;?php
<br /></font><font color="#FF8000">//&nbsp;&nbsp;See comments below (right above the form).
<br />
<br />&nbsp;&nbsp;</font><font color="#007700">if (</font><font color="#0000BB">$mode </font><font color="#007700">== </font><font color="#DD0000">"submit"</font><font color="#007700">) {
<br />&nbsp;&nbsp;&nbsp;&nbsp;if (</font><font color="#0000BB">$enable_html </font><font color="#007700">!= </font><font color="#DD0000">"on"</font><font color="#007700">) {
<br /></font><font color="#FF8000">/*
<br />&nbsp;&nbsp;&nbsp;&nbsp;The user does not want to send the e-mail in HTML format, so we must get
<br />&nbsp;&nbsp;&nbsp;&nbsp;rid of the HTML in the message.
<br />*/
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</font><font color="#0000BB">$mail_body </font><font color="#007700">= </font><font color="#0000BB">htmlspecialchars </font><font color="#007700">(</font><font color="#0000BB">$mail_body</font><font color="#007700">);
<br />&nbsp;&nbsp;&nbsp;&nbsp;}
<br />
<br /></font><font color="#FF8000">//&nbsp;&nbsp;Now we set the headers for our e-mail message.
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;</font><font color="#0000BB">$headers </font><font color="#007700">.= </font><font color="#DD0000">"MIME-Version: 1.0 \n"</font><font color="#007700">;
<br />&nbsp;&nbsp;&nbsp;&nbsp;</font><font color="#0000BB">$headers </font><font color="#007700">.= </font><font color="#DD0000">"Content-type: text/html; charset=iso-8859-1 \n"</font><font color="#007700">;
<br />&nbsp;&nbsp;&nbsp;&nbsp;</font><font color="#0000BB">$headers </font><font color="#007700">.= </font><font color="#DD0000">"from:$mail_from\r\nCc:$mail_cc\r\nBcc:$mail_bcc"</font><font color="#007700">;
<br />
<br /></font><font color="#FF8000">/*
<br />&nbsp;&nbsp;&nbsp;&nbsp;Now it's time to send the message, we'll use the mail () function.
<br />&nbsp;&nbsp;&nbsp;&nbsp;The function will return TRUE on success, FALSE on failure.
<br />&nbsp;&nbsp;&nbsp;&nbsp;We can use that to make sure the e-mail was sent without
<br />&nbsp;&nbsp;&nbsp;&nbsp;any problems.
<br />&nbsp;&nbsp;&nbsp;&nbsp;The "@" in front of the function is optional.&nbsp;&nbsp;In PHP, whenever
<br />&nbsp;&nbsp;&nbsp;&nbsp;there is an @ in front of ANY function, the script will not show
<br />&nbsp;&nbsp;&nbsp;&nbsp;any errors.&nbsp;&nbsp;As we will let the user know if anything goes wrong
<br />&nbsp;&nbsp;&nbsp;&nbsp;ourselves, we don't need PHP to give the errors for us and we can
<br />&nbsp;&nbsp;&nbsp;&nbsp;show the error however we want (not with Warning: ... on line ...).
<br />*/
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;</font><font color="#007700">if (@</font><font color="#0000BB">mail </font><font color="#007700">(</font><font color="#0000BB">$mail_to</font><font color="#007700">, </font><font color="#0000BB">$mail_subject</font><font color="#007700">, </font><font color="#0000BB">$mail_body</font><font color="#007700">, </font><font color="#0000BB">$headers</font><font color="#007700">)) {
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print (</font><font color="#DD0000">"&lt;h1&gt;&lt;font color=\"#004000\"&gt;The e-mail was sent successfully!&lt;/font&gt;&lt;/h1&gt;"</font><font color="#007700">);
<br />&nbsp;&nbsp;&nbsp;&nbsp;} else {
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print (</font><font color="#DD0000">"&lt;h1&gt;&lt;font color=\"#880000\"&gt;An error occurred while sending the e-mail!&lt;/font&gt;&lt;/h1&gt;"</font><font color="#007700">);
<br />&nbsp;&nbsp;&nbsp;&nbsp;}
<br />
<br /></font><font color="#FF8000">//&nbsp;&nbsp;We don't need to show the form again.
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;</font><font color="#007700">exit;
<br />&nbsp;&nbsp;}
<br /></font><font color="#0000BB">?&gt;
<br /></font>
<br />&lt;html&gt;
<br />
<br />&lt;head&gt;
<br />&lt;title&gt;Send e-mail&lt;/title&gt;
<br />&lt;script language="javascript"&gt;
<br />&nbsp;&nbsp;function DoSubmit ()
<br />&nbsp;&nbsp;{
<br />/*
<br />&nbsp;&nbsp;&nbsp;&nbsp;This javascript will check if the important fields have been filled in.
<br />&nbsp;&nbsp;&nbsp;&nbsp;The control is pretty basic (if the user types " " it will see it as full,
<br />&nbsp;&nbsp;&nbsp;&nbsp;but it is enough to alert a person who forgot to fill out a form, without
<br />&nbsp;&nbsp;&nbsp;&nbsp;him / her having to wait until the form refreshes (good for slow modems).
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;The return ""; command will exit the function, so that the form is only
<br />&nbsp;&nbsp;&nbsp;&nbsp;submitted when it is valid.
<br />*/
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;if (document.form.mail_from.value == "") {
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;alert ("You forgot to enter the 'from' field.");
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.form.mail_from.focus ();
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return "";
<br />&nbsp;&nbsp;&nbsp;&nbsp;}
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;if (document.form.mail_to.value == "") {
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;alert ("You forgot to enter the 'to' field.");
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.form.mail_to.focus ();
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return "";
<br />&nbsp;&nbsp;&nbsp;&nbsp;}
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;if (document.form.mail_subject.value == "") {
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;alert ("You forgot to enter the 'subject' field.");
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.form.mail_subject.focus ();
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return "";
<br />&nbsp;&nbsp;&nbsp;&nbsp;}
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;if (document.form.mail_body.value == "") {
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;alert ("You forgot to enter the 'body' field.");
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.form.mail_body.focus ();
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return "";
<br />&nbsp;&nbsp;&nbsp;&nbsp;}
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;document.form.submit ();
<br />&nbsp;&nbsp;}
<br />&lt;/script&gt;
<br />&lt;/head&gt;
<br />
<br />&lt;body&gt;
<br />&lt;!--
<br />&nbsp;&nbsp;&nbsp;&nbsp;By setting the form's action to $PHP_SELF, this code will work even
<br />&nbsp;&nbsp;&nbsp;&nbsp;when you change the name from email.php into whatever you want (.php).
<br />
<br />&nbsp;&nbsp;&nbsp;&nbsp;The included (hidden) field, mode, will be used to see if the user has
<br />&nbsp;&nbsp;&nbsp;&nbsp;submitted the form or if the page is loading for the first time.&nbsp;&nbsp;If the
<br />&nbsp;&nbsp;&nbsp;&nbsp;user has submitted the page, the variable $mode will have the string
<br />&nbsp;&nbsp;&nbsp;&nbsp;"submit" as its value, otherwise the variable will be empty.
<br />--&gt;
<br />&lt;form action="<font color="#0000BB">&lt;?php </font><font color="#007700">print (</font><font color="#0000BB">$PHP_SELF</font><font color="#007700">); </font><font color="#0000BB">?&gt;</font>" method="post" name="form"&gt;
<br />&nbsp;&nbsp;&lt;table&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;From:&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;input type="text" name="mail_from" size="40"&gt;&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;/tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;To:&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;input type="text" name="mail_to" size="40"&gt;&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;/tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;Cc:&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;input type="text" name="mail_cc" size="40"&gt;&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;/tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;Bcc:&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;input type="text" name="mail_bcc" size="40"&gt;&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;/tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;Subject:&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;input type="text" name="mail_subject" size="40"&gt;&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;/tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td valign="top"&gt;Body:&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;textarea name="mail_body" cols="40" rows="10"&gt;&lt;/textarea&gt;&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;/tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;input type="checkbox" name="enable_html"&gt; enable HTML in this message.&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;/tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;tr&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;input type="hidden" name="mode" value="submit"&gt;&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;td&gt;&lt;input type="button" onclick="DoSubmit ()" value="Send e-mail"&gt;&lt;/td&gt;
<br />&nbsp;&nbsp;&nbsp;&nbsp;&lt;/tr&gt;
<br />&nbsp;&nbsp;&lt;/table&gt;
<br />&lt;/form&gt;
<br />
<br />&lt;/body&gt;
<br />
<br />&lt;/html&gt;</font>
</code>

