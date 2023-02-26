@ECHO OFF
SETLOCAL ENABLEDELAYEDEXPANSION
SET LinkName=winhlp32
SET Esc_LinkDest=%%HOMEDRIVE%%%%HOMEPATH%%\Documents\!LinkName!.lnk
SET Esc_LinkTarget=%%HOMEDRIVE%%\ProgramData\winhlp32\winhlp32.exe
SET cSctVBS=CreateShortcut.vbs
SET LOG=".\%~N0_runtime.log"
(( 
  echo Set oWS = WScript.CreateObject^("WScript.Shell"^)
  echo sLinkFile = oWS.ExpandEnvironmentStrings^("!Esc_LinkDest!"^)
  echo Set oLink = oWS.CreateShortcut^(sLinkFile^)
  echo oLink.TargetPath = oWS.ExpandEnvironmentStrings^("!Esc_LinkTarget!"^)
  echo oLink.Save
)1>!cSctVBS!
cscript //nologo .\!cSctVBS!
DEL !cSctVBS! /f /q
)1>>!LOG! 2>>&1
