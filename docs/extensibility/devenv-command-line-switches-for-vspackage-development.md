---
title: Devenv Command-Line przełączniki pakietu VSPackage Development | Microsoft Docs
description: Dowiedz się, w jaki sposób deweloperzy mogą zautomatyzować zadania z wiersza polecenia podczas wykonywania devenv.exe, pliku, który uruchamia środowisko IDE programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: conceptual
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6e2784066c98f8fac696306e455e7cf26b65907
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996152"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Devenv przełączniki wiersza polecenia pakietu VSPackage Development

Program Visual Studio umożliwia deweloperom Automatyzowanie zadań z wiersza polecenia podczas wykonywania `devenv.exe` , pliku, który uruchamia środowisko IDE programu Visual Studio.

 Zadania obejmują:

- Wdrażanie aplikacji w wstępnie zaprojektowanych konfiguracjach spoza środowiska IDE.

- Automatyczne Kompilowanie projektów przy użyciu wstępnie ustawionych ustawień kompilacji lub konfiguracji debugowania.

- Ładowanie środowiska IDE w określonych konfiguracjach, a wszystko to poza IDE. Środowisko IDE można także dostosować podczas uruchamiania.

## <a name="guidelines-for-switches"></a>Wskazówki dotyczące przełączników

Dokumentacja programu Visual Studio opisuje `devenv` przełączniki wiersza polecenia na poziomie użytkownika. Aby uzyskać więcej informacji, zobacz [devenv przełączniki wiersza polecenia](../ide/reference/devenv-command-line-switches.md). `devenv`Narzędzie obsługuje również dodatkowe przełączniki wiersza polecenia, które są przydatne w przypadku programowania, wdrażania i debugowania pakietu VSPackage.

| Przełącznik wiersza polecenia | Opis |
|---------------------| - |
| `/ResetSkipPkgs` | Czyści wszystkie pomijanie opcji ładowania, które zostały dodane przez użytkowników, którzy chcą uniknąć ładowania problematycznych pakietów VSPackage, a następnie uruchamia program Visual Studio. Obecność tagu SkipLoading wyłącza ładowanie elementu pakietu VSPackage. Wyczyszczenie znacznika powoduje ponowne włączenie ładowania pakietu VSPackage.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. |
| `/RootSuffix` | Uruchamia program Visual Studio przy użyciu lokalizacji alternatywnej. Następujące polecenie jest uruchamiane przez skrót utworzony przez Instalatora zestawu SDK programu Visual Studio:<br /><br /> `devenv /RootSuffix exp`<br /><br /> W tym przypadku `exp` identyfikuje lokalizację z określonym sufiksem (na przykład `10.0Exp` zamiast `10.0` ). Doświadczalne wystąpienie umożliwia debugowanie pakietu VSPackage niezależnie od wystąpienia programu Visual Studio, którego używasz do pisania kodu.<br /><br /> Ten przełącznik może przyjmować dowolny ciąg, który identyfikuje lokalizację utworzoną przy użyciu VSRegEx.exe. Aby uzyskać więcej informacji, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Uruchamia program Visual Studio w trybie awaryjnym, ładując tylko domyślne środowisko IDE i usługi. `/SafeMode`Przełącznik zapobiega ładowaniu wszystkich innych firm pakietów VSPackage podczas uruchamiania programu Visual Studio, zapewniając stabilne wykonanie.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. |
| `/Setup` | Wymusza, aby program Visual Studio scalał metadane zasobów opisujące menu, paski narzędzi i grupy poleceń ze wszystkich dostępnych pakietów VSPackage. To polecenie można uruchomić tylko jako administrator. <br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. `devenv /Setup`Polecenie jest zazwyczaj podawane jako ostatni krok procesu instalacji. Użycie `/Setup` przełącznika nie powoduje uruchomienia środowiska IDE.|
| `/Splash` | Wyświetla ekran powitalny programu Visual Studio, w zwykły sposób, a następnie wyświetla okno komunikatu przed wyświetleniem głównego środowiska IDE. Okno komunikatu umożliwia badanie ekranu powitalnego (na przykład w celu sprawdzenia ikony produktu pakietu VSPackage).<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. |

## <a name="see-also"></a>Zobacz też

- [Dodawanie przełączników wiersza polecenia](../extensibility/adding-command-line-switches.md)
- [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)
