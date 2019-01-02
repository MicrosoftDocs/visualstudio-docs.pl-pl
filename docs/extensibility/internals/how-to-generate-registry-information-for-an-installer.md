---
title: 'Instrukcje: Generowanie informacji rejestru dla Instalatora | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
- VSPackages, registration manifests
ms.assetid: b1b41012-a777-4ccf-81a6-3b41f0e96583
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f66df6b19e3c47151907ffad04072c378fd1a8fd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875397"
---
# <a name="how-to-generate-registry-information-for-an-installer"></a>Instrukcje: Generowanie informacji rejestru dla Instalatora
*RegPkg.exe* narzędzie może służyć do generowania manifestu rejestracji dla zarządzanych pakietu VSPackage. Manifest może być dołączany do pakietu instalacyjnego Instalatora Windows. RegPkg również można wygenerować pliku, który może być dołączony do pliku źródłowego instalacji na podstawie [zestaw narzędzi XML Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=62238).  
  
> [!IMPORTANT]
>  RegPkg generuje nazwy ścieżek, które są specyficzne dla systemu dla deweloperów, dlatego za każdym razem, gdy używasz RegPkg, należy zmodyfikować dane wyjściowe, aby użyć odpowiedniego Instalatora Windows sformatowane właściwości. Na przykład `InprocServer32` . wartość powinna być  *\<SystemFolder\>mscoree.dll* i ścieżek należy używać *\<#filekey\>* i  *\<$componentkey\>*. Dostosowywanie danych wyjściowych w ten sposób obsługuje komputery przy użyciu Windows zainstalowany na innym dysku lub w innym katalogu, katalogu wersji zlokalizowanych nazw i ścieżek, które użytkownicy mogą wybrać. Aby uzyskać więcej informacji, zobacz [sformatowany](http://go.microsoft.com/fwlink/?LinkId=71120) w zestawie SDK Instalatora Windows. Jeśli możesz konwencjami RegPkg dla Twojej ścieżki systemu rozwoju — na przykład plik identyfikatory formularza *File_\<filename\>*— należy wprowadzić zmiany mniejszej liczby.  
  
### <a name="to-create-a-registration-manifest"></a>Aby utworzyć manifest rejestracji  
  
-   Uruchom RegPkg z **/regfile razem** przełącznika. Podaj inne przełączniki, nazwa pliku wyjściowego i ścieżkę pakietu VSPackage.  
  
     Na przykład w wierszu polecenia należy wpisać podobny do poniższego:  
  
    ```  
    <Visual Studio SDK installation path>\VisualStudioIntegration\Tools\Bin\RegPkg /regfile:MyRegFile.reg MyPackage.dll  
    ```  
  
### <a name="to-view-a-registration-manifest"></a>Aby wyświetlić manifest rejestracji  
  
-   Otwórz manifest rejestracji w dowolnym edytorze tekstów.  
  
     Poniższy przykład to manifest rejestracji, który RegPkg tworzy dla usługi w języka IronPython:  
  
    ```  
    REGEDIT4  
  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python]  
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"  
    "DisplayName"="131"  
    "IndexPath"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\SnippetsIndex.xml"  
    "LangStringId"="python"  
    "Package"="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"  
    "ShowRoots"=dword:00000000  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\ForceCreateDirs]  
    "Python"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\Paths]  
    "Python"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}]  
    @="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage, IronPython.LanguageService, Version=1.0.2373.36479, Culture=neutral, PublicKeyToken=null"  
    "InprocServer32"="C:\\WINNT\\system32\\mscoree.dll"  
    "Class"="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage"  
    "Assembly"="IronPython.LanguageService, Version=1.0.2373.36479, Culture=neutral, PublicKeyToken=null"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\File Extensions]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\File Extensions\.py]  
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\Language Services]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\Language Services\Python]  
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"  
    "Package"="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"  
    "LangResID"=dword:00000064  
    "ShowMatchingBrace"=dword:00000001  
    "CodeSense"=dword:00000001  
    "MatchBraces"=dword:00000001  
    "EnableCommenting"=dword:00000001  
    "ShowCompletion"=dword:00000001  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}]  
    "ID"=dword:00000001  
    "MinEdition"="standard"  
    "ProductVersion"="1.0"  
    "ProductName"="Visual Studio Integration of IronPython Language Service"  
    "CompanyName"="Microsoft Corporation"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services\{923b4811-26e4-4347-ac8a-244762798e1c}]  
    @="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"  
    "Name"="IPythonLibraryManager"  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services]  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services\{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}]  
    @="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"  
    "Name"="Python"  
  
    ```  
  
### <a name="to-create-a-windows-installer-xml-toolset-include-file"></a>Aby utworzyć XML Instalatora Windows narzędzi Dołącz plik  
  
-   Uruchom RegPkg z **/wixfile** przełącznika. Podaj inne przełączniki, nazwa pliku wyjściowego i ścieżkę pakietu VSPackage.  
  
     Na przykład w wierszu polecenia należy wpisać podobny do poniższego:  
  
    ```  
    <Visual Studio SDK installation path>\VisualStudioIntegration\Tools\Bin\RegPkg /codebase /wixfile:IronPython.LanguageService.wxi ..\bin\Release\IronPython.LanguageService.dll  
    ```  
  
### <a name="to-view-a-windows-installer-xml-toolset-include-file"></a>Aby wyświetlić XML Instalatora Windows narzędzi dołączyć plik  
  
-   Otwórz zestaw narzędzi XML Instalatora Windows umieścić plik w dowolnym edytorze tekstów.  
  
     Poniższy przykład jest pliku dołączonego, który tworzy RegPkg dla usługi w języka IronPython:  
  
    ```  
    <Include>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\IntellisenseProviders\IronPythonCodeProvider">  
        <Registry Name="GUID" Value="{9c1807ea-d222-4775-afa8-c092c580e451}" Type="string" />  
        <Registry Name="AddItemLanguageName" Value="Iron Python" Type="string" />  
        <Registry Name="DefaultExtension" Value=".py" Type="string" />  
        <Registry Name="ShortLanguageName" Value="IronPython;Python" Type="string" />  
        <Registry Name="TemplateFolderName" Value="IronPython" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string">  
        <Registry Name="DisplayName" Value="131" Type="string" />  
        <Registry Name="IndexPath" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\SnippetsIndex.xml" Type="string" />  
        <Registry Name="LangStringId" Value="python" Type="string" />  
        <Registry Name="Package" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string" />  
        <Registry Name="ShowRoots" Value="0" Type="integer" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\ForceCreateDirs">  
        <Registry Name="Python" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\Paths">  
        <Registry Name="Python" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\File Extensions\.py" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string" />  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\Language Services\Python" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string">  
        <Registry Name="Package" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string" />  
        <Registry Name="LangResID" Value="100" Type="integer" />  
        <Registry Name="ShowCompletion" Value="1" Type="integer" />  
        <Registry Name="ShowMatchingBrace" Value="1" Type="integer" />  
        <Registry Name="CodeSense" Value="1" Type="integer" />  
        <Registry Name="MatchBraces" Value="1" Type="integer" />  
        <Registry Name="EnableCommenting" Value="1" Type="integer" />  
        <Registry Name="DefaultToInsertSpaces" Value="1" Type="integer" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage, IronPython.LanguageService, Version=1.0.2394.27719, Culture=neutral, PublicKeyToken=null" Type="string">  
        <Registry Name="InprocServer32" Value="[SystemFolder]mscoree.dll" Type="string" />  
        <Registry Name="Class" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage" Type="string" />  
        <Registry Name="CodeBase" Value="[#File_IronPython.LanguageService.dll]" Type="string" />  
        <Registry Name="ID" Value="1" Type="integer" />  
        <Registry Name="MinEdition" Value="standard" Type="string" />  
        <Registry Name="ProductVersion" Value="1.0" Type="string" />  
        <Registry Name="ProductName" Value="Visual Studio Integration of IronPython Language Service" Type="string" />  
        <Registry Name="CompanyName" Value="Microsoft Corporation" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\CLSID\{9c1807ea-d222-4775-afa8-c092c580e451}" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonIntellisenseProvider" Type="string">  
        <Registry Name="InprocServer32" Value="[SystemFolder]mscoree.dll" Type="string" />  
        <Registry Name="Class" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonIntellisenseProvider" Type="string" />  
        <Registry Name="CodeBase" Value="[#File_IronPython.LanguageService.dll]" Type="string" />  
        <Registry Name="ThreadingModel" Value="Both" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Services\{923b4811-26e4-4347-ac8a-244762798e1c}" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string">  
        <Registry Name="Name" Value="IPythonLibraryManager" Type="string" />  
      </Registry>  
  
      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Services\{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string">  
        <Registry Name="Name" Value="Python" Type="string" />  
      </Registry>  
    </Include>  
    ```  
  
## <a name="see-also"></a>Zobacz także  
 [Rejestrowanie pakietów VSPackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Pakiety VSPackage](../../extensibility/internals/vspackages.md)