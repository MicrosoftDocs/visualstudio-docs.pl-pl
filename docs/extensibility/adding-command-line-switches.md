---
title: Dodawanie przełączników wiersza polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 376dcee6f23ec2633efe1b23f77552ebf33341f2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722606"
---
# <a name="add-command-line-switches"></a>Dodawanie przełączników wiersza polecenia
Możesz dodać przełączniki wiersza polecenia, które są stosowane do Twojego pakietu VSPackage podczas *devenv.exe* jest wykonywany. Użyj <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> do deklarowania nazwę przełącznika i jego właściwości. W tym przykładzie przełącznika MySwitch zostanie dodany do podklasy pakietu VSPackage o nazwie **AddCommandSwitchPackage** bez argumentów i za pomocą pakietu VSPackage ładowane automatycznie.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Parametry nazwane są wyświetlane w następujących opisach.

||||
|-|-|-|-|
| Parametr | Opis|
| Argumenty | Liczba argumentów dla przełącznika. Może być "*", lub Podaj listę argumentów. |
| DemandLoad | Ładowanie pakietu VSPackage automatycznie, jeśli jest ono ustawione na 1, w przeciwnym razie jest ustawiona na 0. |
| HelpString — | Pomoc ciąg lub identyfikator zasobu ciągu do wyświetlania o **devenv /?**. |
| Nazwa | Przełącznik. |
| PackageGuid | Identyfikator GUID pakietu. |

 Pierwsza wartość argumentów jest zwykle 0 lub 1. Specjalna wartość elementu "*" może służyć do wskazania, że całą pozostałą część wiersza polecenia jest argumentem. Może to być przydatne podczas debugowania scenariuszy, w którym użytkownik musi przejść w ciągu polecenia debugera.

 Wartość DemandLoad jest albo `true` (1) lub `false` (0) oznacza, że pakietu VSPackage powinny być załadowane automatycznie.

 Wartość HelpString — jest identyfikator zasobu ciągu, który pojawia się w **devenv /?** Wyświetlanie pomocy. Ta wartość powinna być w formie "#nnn" gdzie nnn jest liczbą całkowitą. Wartość ciągu w pliku zasobów powinien kończyć się znakiem nowego wiersza.

 Wartość nazwy jest nazwa przełącznika.

 Wartość PackageGuid jest identyfikator GUID pakietu, który implementuje ten przełącznik. IDE używa tego identyfikatora GUID w celu odnalezienia pakietu VSPackage w rejestrze, do której stosują się przełącznik wiersza polecenia.

## <a name="retrieve-command-line-switches"></a>Pobieranie przełączniki wiersza polecenia
 Po załadowaniu pakietu można pobrać przełączniki wiersza polecenia, wykonując następujące kroki.

1. W swojej VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementacji, wywołanie `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> można pobrać <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfejsu.

2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> można pobrać przełączniki wiersza polecenia, które użytkownik wprowadził.

   Poniższy kod przedstawia sposób dowiedzieć się, czy przełącznik wiersza polecenia MySwitch została wprowadzona przez użytkownika:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Jest odpowiedzialny za sprawdzaj przełączniki wiersza polecenia w każdym razem, gdy jest ładowany do pakietu.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)
- [Narzędzie CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [.Pkgdef files](/visualstudio/extensibility/shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file)