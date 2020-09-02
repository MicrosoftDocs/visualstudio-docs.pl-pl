---
title: Dodawanie przełączników wiersza polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562279"
---
# <a name="adding-command-line-switches"></a>Dodawanie przełączników wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas wykonywania devenv.exe można dodać przełączniki wiersza polecenia, które są stosowane do pakietu VSPackage. Użyj <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> , aby zadeklarować nazwę przełącznika i jego właściwości. W tym przykładzie przełącznik przełącznika zostanie dodany dla podklasy pakietu VSPackage o nazwie **AddCommandSwitchPackage** bez argumentów i z pakietu VSPackage załadowany automatycznie.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Parametry nazwane są pokazane w poniższej tabeli.  
  
 Argumenty  
 Liczba argumentów dla przełącznika. Może mieć wartość "*" lub listę argumentów.  
  
 Na DemandLoad  
 Załaduj pakietu VSPackage automatycznie, jeśli jest ustawiona na 1, w przeciwnym razie ustaw wartość 0.  
  
 HelpString  
 Ciąg pomocy lub identyfikator zasobu ciągu do wyświetlania z **devenv/?**.  
  
 Nazwa  
 Przełącznik.  
  
 PackageGuid  
 Identyfikator GUID pakietu.  
  
 Pierwsza wartość argumentów jest zwykle równa 0 lub 1. Specjalna wartość "*" może służyć do wskazania, że cały pozostała część wiersza polecenia jest argumentem. Może to być przydatne w scenariuszach debugowania, w których użytkownik musi przekazać ciąg poleceń debugera.  
  
 Wartość na DemandLoad jest `true` (1) lub `false` (0) wskazuje, że pakietu VSPackage powinien zostać załadowany automatycznie.  
  
 Wartość HelpString jest IDENTYFIKATORem zasobu ciągu, który pojawia się w devenv/? Wyświetl pomoc. Ta wartość powinna mieć postać "#nnn", gdzie NNN jest liczbą całkowitą. Wartość ciągu w pliku zasobu powinna kończyć się znakiem nowego wiersza.  
  
 Wartość nazwa to nazwa przełącznika.  
  
 Wartość PackageGuid jest identyfikatorem GUID pakietu, który implementuje ten przełącznik. IDE używa tego identyfikatora GUID, aby znaleźć pakietu VSPackage w rejestrze, do którego ma zastosowanie przełącznik wiersza polecenia.  
  
## <a name="retrieving-command-line-switches"></a>Pobieranie przełączników wiersza polecenia  
 Po załadowaniu pakietu można pobrać przełączniki wiersza polecenia, wykonując następujące kroki.  
  
1. W implementacji programu pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Wywołaj metodę `QueryService` w <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> celu uzyskania <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfejsu.  
  
2. Wywołaj, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> Aby pobrać przełączniki wiersza polecenia wprowadzone przez użytkownika.  
  
   Poniższy kod pokazuje, jak dowiedzieć się, czy przełącznik wiersza polecenia "onswitch" został wprowadzony przez użytkownika:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Ponosisz odpowiedzialność za sprawdzanie przełączników wiersza polecenia przy każdym załadowaniu pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Przełączniki wiersza polecenia devenv](../ide/reference/devenv-command-line-switches.md)   
 [Narzędzie CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [Pliki .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
