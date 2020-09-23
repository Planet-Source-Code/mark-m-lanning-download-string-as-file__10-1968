<div align="center">

## Download String as File


</div>

### Description

This may seem simple but I didn't find anything like this anywhere and I thought I should add it so it will help others.

This artitle is to show you how to send a string variable as a downloadable file in asp.net.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Mark M\. Lanning](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/mark-m-lanning.md)
**Level**          |Beginner
**User Rating**    |5.0 (20 globes from 4 users)
**Compatibility**  |ASP\.NET
**Category**       |[Files](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files__10-2.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/mark-m-lanning-download-string-as-file__10-1968/archive/master.zip)





### Source Code

<p></P>
<p></P>
To send a string variable to the client as a downloadable file you must first convert the string data over to a byte array... once in a byte array you can send the byte array to the client.
Here is the code that will send a string as a file to the client:
 <font SIZE="2" COLOR="#0000ff">
<p>Public</font><font SIZE="2"> </font><font SIZE="2" COLOR="#0000ff">Function</font><font SIZE="2">
SendFileToClient(</font><font SIZE="2" COLOR="#0000ff">ByRef</font><font SIZE="2">
WebPage </font><font SIZE="2" COLOR="#0000ff">As</font><font SIZE="2"> UI.Page,
</font><font SIZE="2" COLOR="#0000ff">ByVal</font><font SIZE="2"> strFileData
</font><font SIZE="2" COLOR="#0000ff">As</font><font SIZE="2"> </font>
<font SIZE="2" COLOR="#0000ff">String</font><font SIZE="2">, </font>
<font SIZE="2" COLOR="#0000ff">ByVal</font><font SIZE="2"> strFileName </font>
<font SIZE="2" COLOR="#0000ff">As</font><font SIZE="2"> </font>
<font SIZE="2" COLOR="#0000ff">String</font><font SIZE="2">) </font>
<font SIZE="2" COLOR="#0000ff">As</font><font SIZE="2"> </font>
<font SIZE="2" COLOR="#0000ff">Boolean</p>
</font><font SIZE="2">
<p></font><font SIZE="2" COLOR="#0000ff">    Try</p>
</font><font SIZE="2">
<p>        </font>
<font SIZE="2" COLOR="#008000">'convert the passed file string to a byte array<br>
</font><font SIZE="2" COLOR="#0000ff">       
Dim</font><font SIZE="2"> byteArray() </font><font SIZE="2" COLOR="#0000ff">As</font><font SIZE="2">
</font><font SIZE="2" COLOR="#0000ff">Byte</font><font SIZE="2"> =
System.Text.Encoding.ASCII.GetBytes(strFileData)</p>
<p></font><font SIZE="2" COLOR="#008000">       
'send the data to the client<br>
</font><font SIZE="2">       
WebPage.Response.Clear()<br>
        WebPage.Response.ContentType =
"text/plain"<br>
        WebPage.Response.AddHeader("Content-Disposition",
"attachment;filename=" & strFileName & ";")<br>
       
WebPage.Response.BinaryWrite(byteArray)<br>
        WebPage.Response.End()</p>
<p></font><font SIZE="2" COLOR="#0000ff">    Catch</font><font SIZE="2">
ex </font><font SIZE="2" COLOR="#0000ff">As</font><font SIZE="2"> Exception</p>
<p>        </font>
<font SIZE="2" COLOR="#008000">'trap the error and return false saying that
something happened<br>
</font><font SIZE="2">        </font>
<font SIZE="2" COLOR="#0000ff">Return</font><font SIZE="2"> </font>
<font SIZE="2" COLOR="#0000ff">False</p>
</font><font SIZE="2">
<p></font><font SIZE="2" COLOR="#0000ff">    End</font><font SIZE="2">
</font><font SIZE="2" COLOR="#0000ff">Try</p>
</font><font SIZE="2">
<p>    </font><font SIZE="2" COLOR="#008000">'if success then
return true<br>
</font><font SIZE="2">    </font><font SIZE="2" COLOR="#0000ff">
Return</font><font SIZE="2"> </font><font SIZE="2" COLOR="#0000ff">True</p>
</font><font SIZE="2">
<p></font><font SIZE="2" COLOR="#0000ff">End</font><font SIZE="2"> </font>
<font SIZE="2" COLOR="#0000ff">Function</p>
</font>
That is it.. just pass the function the string and the filename you want to be specified and bingo.
So the function call would look something like this:
<p></P>
</font><font SIZE="2" COLOR="#008000">
<p>'send the file data to the client<br>
</font><font SIZE="2" COLOR="#0000ff">Call</font><font SIZE="2">
SendFileToClient(</font><font SIZE="2" COLOR="#0000ff">Me</font><font SIZE="2">,
mExportData, "Export.csv")</p>
</font>
<p></P>

