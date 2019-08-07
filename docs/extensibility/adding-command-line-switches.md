---
title: Dodawanie przełączników wiersza polecenia | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c44864285f3e5701604379a110292c29d3f9b78
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821535"
---
# <a name="add-command-line-switches"></a>Dodawanie przełączników wiersza polecenia
Można dodać przełączniki wiersza polecenia, które są stosowane do pakietu VSPackage podczas wykonywania *devenv. exe* . Użyj <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> , aby zadeklarować nazwę przełącznika i jego właściwości. W tym przykładzie przełącznik przełącznika zostanie dodany dla podklasy pakietu VSPackage o nazwie **AddCommandSwitchPackage** bez argumentów i z pakietu VSPackage załadowany automatycznie.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Nazwane parametry są pokazane w następujących opisach.

||||
|-|-|-|-|
| Parametr | Opis|
| Argumenty | Liczba argumentów dla przełącznika. Może mieć wartość "*" lub listę argumentów. |
| Na DemandLoad | Załaduj pakietu VSPackage automatycznie, jeśli jest ustawiona na 1, w przeciwnym razie ustaw wartość 0. |
| HelpString | Ciąg pomocy lub identyfikator zasobu ciągu do wyświetlania z **devenv/?** . |
| Nazwa | Przełącznik. |
| PackageGuid | Identyfikator GUID pakietu. |

 Pierwsza wartość argumentów jest zwykle równa 0 lub 1. Specjalna wartość "*" może służyć do wskazania, że cały pozostała część wiersza polecenia jest argumentem. Może to być przydatne w scenariuszach debugowania, w których użytkownik musi przekazać ciąg poleceń debugera.

 Wartość na DemandLoad jest `true` (1) lub `false` (0) wskazuje, że pakietu VSPackage powinien zostać załadowany automatycznie.

 Wartość HelpString jest IDENTYFIKATORem zasobu ciągu, który pojawia się w **devenv/?** Wyświetl pomoc. Ta wartość powinna mieć postać "#nnn", gdzie NNN jest liczbą całkowitą. Wartość ciągu w pliku zasobu powinna kończyć się znakiem nowego wiersza.

 Wartość nazwa to nazwa przełącznika.

 Wartość PackageGuid jest identyfikatorem GUID pakietu, który implementuje ten przełącznik. IDE używa tego identyfikatora GUID, aby znaleźć pakietu VSPackage w rejestrze, do którego ma zastosowanie przełącznik wiersza polecenia.

## <a name="retrieve-command-line-switches"></a>Pobierz przełączniki wiersza polecenia
 Po załadowaniu pakietu można pobrać przełączniki wiersza polecenia, wykonując następujące kroki.

1. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementacji programu pakietu VSPackage Wywołaj metodę `QueryService` w <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> celu uzyskania <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfejsu.

2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> , aby pobrać przełączniki wiersza polecenia wprowadzone przez użytkownika.

   Poniższy kod pokazuje, jak dowiedzieć się, czy przełącznik wiersza polecenia "onswitch" został wprowadzony przez użytkownika:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Ponosisz odpowiedzialność za sprawdzanie przełączników wiersza polecenia przy każdym załadowaniu pakietu.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Przełączniki wiersza polecenia devenv](../ide/reference/devenv-command-line-switches.md)
- [Narzędzie CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [.Pkgdef files](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)