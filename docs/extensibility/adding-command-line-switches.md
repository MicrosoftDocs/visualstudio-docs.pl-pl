---
title: Dodawanie przełączników wiersza polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740168"
---
# <a name="add-command-line-switches"></a>Dodawanie przełączników wiersza polecenia
Można dodać przełączniki wiersza polecenia, które mają zastosowanie do vspackage podczas *wykonywania devenv.exe.* Służy <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> do deklarowania nazwy przełącznika i jego właściwości. W tym przykładzie przełącznik MySwitch jest dodawany dla podklasy VSPackage o nazwie **AddCommandSwitchPackage** bez argumentów i z VSPackage załadowany automatycznie.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Nazwane parametry są wyświetlane w poniższych opisach.

||||
|-|-|-|-|
| Parametr | Opis|
| Argumenty | Liczba argumentów dla przełącznika. Może to być "*" lub lista argumentów. |
| Obciążenie popytem | Załaduj VSPackage automatycznie, jeśli jest ustawiona na 1, w przeciwnym razie ustawiona na 0. |
| Helpstring | Ciąg pomocy lub identyfikator zasobu ciągu do wyświetlenia z **devenv /?**. |
| Nazwa | Przełącznik. |
| PakietGuid | Identyfikator GUID pakietu. |

 Pierwszą wartością argumentów jest zwykle 0 lub 1. Specjalna wartość "*" może służyć do wskazania, że cała reszta wiersza polecenia jest argumentem. Może to być przydatne w przypadku scenariuszy debugowania, w których użytkownik musi przekazać w ciągu polecenia debugera.

 DemandLoad Wartość jest `true` (1) `false` lub (0) wskazuje, że VSPackage powinny być ładowane automatycznie.

 Wartość HelpString jest identyfikatorem zasobu ciągu, który pojawia się w **devenv /?** Wyświetlacz pomocy. Ta wartość powinna być w postaci "#nnn", gdzie nnn jest całkowitej liczby. Wartość ciągu w pliku zasobu powinna kończyć się nowym znakiem wiersza.

 Name Value jest nazwą przełącznika.

 PackageGuid wartość jest identyfikator GUID pakietu, który implementuje ten przełącznik. IDE używa tego identyfikatora GUID, aby znaleźć VSPackage w rejestrze, do którego stosuje się przełącznik wiersza polecenia.

## <a name="retrieve-command-line-switches"></a>Pobieranie przełączników wiersza polecenia
 Po załadowaniu pakietu można pobrać przełączniki wiersza polecenia, wykonując następujące kroki.

1. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementacji VSPackage `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> wywołać, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> uzyskać interfejs.

2. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> w celu pobrania przełączników wiersza polecenia wprowadzonych przez użytkownika.

   Poniższy kod pokazuje, jak dowiedzieć się, czy przełącznik wiersza polecenia MySwitch został wprowadzony przez użytkownika:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Twoim obowiązkiem jest sprawdzanie przełączników wiersza polecenia za każdym razem, gdy pakiet jest ładowany.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)
- [Narzędzie CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Pliki Pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
