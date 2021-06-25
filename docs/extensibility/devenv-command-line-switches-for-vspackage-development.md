---
title: Przełączniki devenv Command-Line do tworzenia pakietów VSPackage | Microsoft Docs
description: Dowiedz się, jak deweloperzy mogą automatyzować zadania z wiersza polecenia podczas devenv.exe, czyli pliku, który uruchamia Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4ea08b4714a79e09fce5933b67997a032532481f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904246"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Przełączniki wiersza polecenia Devenv do tworzenia pakietów VSPackage

Visual Studio umożliwia deweloperom automatyzowanie zadań z wiersza polecenia podczas wykonywania polecenia , czyli pliku, który uruchamia `devenv.exe` Visual Studio IDE.

 Zadania obejmują:

- Wdrażanie aplikacji w wstępnie zaprojektowanych konfiguracjach spoza środowiska IDE.

- Automatyczne kompilowanie projektów przy użyciu wstępnie ustawionych ustawień kompilacji lub konfiguracji debugowania.

- Ładowanie środowiska IDE w określonych konfiguracjach, a wszystko to spoza środowiska IDE. Możesz również dostosować idee po uruchomieniu.

## <a name="guidelines-for-switches"></a>Wytyczne dotyczące przełączników

Visual Studio dokumentacji opisano przełączniki wiersza polecenia `devenv` na poziomie użytkownika. Aby uzyskać więcej informacji, zobacz [Devenv command-line switches (Przełączniki wiersza polecenia Devenv).](../ide/reference/devenv-command-line-switches.md) Narzędzie `devenv` obsługuje również dodatkowe przełączniki wiersza polecenia, które są przydatne podczas tworzenia, wdrażania i debugowania pakietu VSPackage.

| Przełącznik wiersza polecenia | Opis |
|---------------------| - |
| `/ResetSkipPkgs` | Umożliwia wyczyszczenie wszystkich opcji pomijania ładowania dodanych przez użytkowników, którzy chcą uniknąć ładowania problematycznych pakietów VSPackage, a następnie uruchamia Visual Studio. Obecność tagu SkipLoading powoduje wyłączenie ładowania pakietów VSPackage. Wyczyszczenie tagu ponownie włącza ładowanie pakietów VSPackage.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. |
| `/RootSuffix` | Rozpoczyna Visual Studio przy użyciu lokalizacji alternatywnej. Następujące polecenie jest uruchamiane przez skrót utworzony przez instalatora Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> W tym przypadku program `exp` identyfikuje lokalizację z określonym sufiksem (na przykład `10.0Exp` zamiast `10.0` ). Wystąpienie eksperymentalne umożliwia debugowanie pakietów VSPackage niezależnie od wystąpienia Visual Studio, za pomocą których piszesz kod.<br /><br /> Ten przełącznik może przyjmować dowolny ciąg, który identyfikuje lokalizację utworzoną przy użyciu VSRegEx.exe. Aby uzyskać więcej informacji, zobacz [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Uruchamia Visual Studio w trybie awaryjnym, ładując tylko domyślne środowiska IDE i usługi. Przełącznik zapobiega ładowaniu wszystkich pakietów VSPackage innych firm `/SafeMode` po Visual Studio, zapewniając stabilne wykonywanie.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. |
| `/Setup` | Wymusza Visual Studio do scalania metadanych zasobów, które opisują menu, paski narzędzi i grupy poleceń ze wszystkich dostępnych pakietów VSPackage. To polecenie można uruchomić tylko jako administrator. <br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. Polecenie `devenv /Setup` jest zazwyczaj podawane jako ostatni krok procesu instalacji. Użycie `/Setup` przełącznika nie uruchamia środowiska IDE.|
| `/Splash` | Pokazuje Visual Studio ekranu powitalnego, jak zwykle, a następnie wyświetla okno komunikatu przed pokazaniem głównego środowiska IDE. Okno komunikatu umożliwia sprawdzenie ekranu powitalnego (na przykład w celu sprawdzenia ikony produktu VSPackage).<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. |

## <a name="see-also"></a>Zobacz też

- [Dodawanie przełączników wiersza polecenia](../extensibility/adding-command-line-switches.md)
- [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)
