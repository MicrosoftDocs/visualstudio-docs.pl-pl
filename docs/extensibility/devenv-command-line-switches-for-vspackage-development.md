---
title: Przełączniki wiersza polecenia Devenv dla programowania pakietu VSPackage | Dokumentacja firmy Microsoft
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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd95fe31949b51c7167337ad21c51251e84a19a7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864065"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Przełączniki wiersza polecenia Devenv dla programowania pakietu VSPackage

Program Visual Studio umożliwia deweloperom Automatyzowanie zadań przy użyciu wiersza polecenia podczas wykonywania `devenv.exe`, plik, który uruchamia środowiska IDE programu Visual Studio.

 Zadania obejmują:

- Wdrażanie aplikacji w wstępnie zdefiniowanych konfiguracji z poza IDE.

- Automatyczne kompilowanie projektów za pomocą wstępnie ustawionych ustawienia kompilacji lub konfiguracji debugowania.

- Ładowanie środowiska IDE w określonej konfiguracji, wszystko poza IDE. Można również dostosować IDE po uruchomieniu.

## <a name="guidelines-for-switches"></a>Wytyczne dotyczące przełączników

Dokumentacja programu Visual Studio w tym artykule opisano poziomu użytkownika `devenv` przełączniki wiersza polecenia. Aby uzyskać więcej informacji, zobacz [przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md). `devenv` Narzędzie obsługuje również dodatkowe przełączniki wiersza polecenia, które są przydatne w przypadku pakietu VSPackage programowania, wdrażania i debugowania.

| Przełącznik wiersza polecenia | Opis |
|---------------------| - |
| `/ResetSkipPkgs` | Czyści wszystkie opcje ładowania Pomiń dodanych przez użytkowników, którzy pozwala uniknąć wczytywania problematyczne pakietów VSPackage, a następnie uruchamia programu Visual Studio. Obecność tagu SkipLoading powoduje wyłączenie ładowania pakietu VSPackage. Czyszczenie tagu włączające ładowania pakietu VSPackage.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. |
| `/RootSuffix` | Uruchamia programu Visual Studio za pomocą alternatywnej lokalizacji. Następujące polecenie jest uruchamiane przez skrót utworzony przez Instalatora programu Visual Studio SDK:<br /><br /> `devenv /RootSuffix exp`<br /><br /> W tym przypadku `exp` identyfikuje lokalizację przy użyciu określonego sufiksu (na przykład `10.0Exp` zamiast `10.0`). Wystąpienie eksperymentalne umożliwia debugowanie pakietu VSPackage niezależnie od wystąpienia programu Visual Studio, którego używasz do pisania kodu.<br /><br /> Ten przełącznik może być dowolny ciąg, który określa lokalizację, który został utworzony przy użyciu VSRegEx.exe. Aby uzyskać więcej informacji, zobacz [wystąpienie doświadczalne](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Powoduje uruchomienie programu Visual Studio w trybie awaryjnym, ładowanie tylko domyślne środowisko IDE i usługi. `/SafeMode` Przełącznik zapobiega ładowania po uruchomieniu programu Visual Studio, zapewniając stabilne wykonanie wszystkich innych pakietów VSPackage.<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. |
| `/Setup` | Wymusza Visual Studio, aby scalić metadane zasobu, który opisuje menu, paski narzędzi i grup poleceń z wszystkich dostępnych pakietów VSPackage. To polecenie można uruchomić tylko z uprawnieniami administratora. <br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. `devenv /Setup` Polecenia jest zazwyczaj podawana jako ostatni krok w procesie instalacji programu. Korzystanie z `/Setup` przełącznika nie zaczyna się IDE.|
| `/Splash` | Pokazuje powitalny programu Visual Studio, ekranu w zwykły sposób, a następnie przedstawiono komunikat polu przed wyświetleniem głównego środowiska IDE. W oknie komunikatu umożliwia badanie ekran powitalny (na przykład, aby sprawdzić, czy ikona produktu pakietu VSPackage).<br /><br /> Ten przełącznik nie przyjmuje żadnych argumentów. |

## <a name="see-also"></a>Zobacz także

- [Dodawanie przełączników wiersza polecenia](../extensibility/adding-command-line-switches.md)
- [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)