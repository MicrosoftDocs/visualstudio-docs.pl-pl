---
title: Przełączniki linii poleceń Devenv dla rozwoju VSPackage | Dokumenty firmy Microsoft
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
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712193"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Przełączniki wiersza polecenia Devenv dla rozwoju VSPackage

Visual Studio umożliwia deweloperom zautomatyzować zadania z `devenv.exe`wiersza polecenia podczas wykonywania pliku, który uruchamia IDE programu Visual Studio.

 Zadania obejmują:

- Wdrażanie aplikacji w wstępnie skonfigurowanych konfiguracjach spoza IDE.

- Automatyczne tworzenie projektów przy użyciu ustawień kompilacji predefiniowanych lub konfiguracji debugowania.

- Ładowanie IDE w określonych konfiguracjach, wszystkie spoza IDE. Ide można również dostosować po uruchomieniu.

## <a name="guidelines-for-switches"></a>Wskazówki dotyczące przełączników

W dokumentacji programu Visual `devenv` Studio opisano przełączniki wiersza polecenia na poziomie użytkownika. Aby uzyskać więcej informacji, zobacz [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md). Narzędzie `devenv` obsługuje również dodatkowe przełączniki wiersza polecenia, które są przydatne w programie VSPackage rozwoju, wdrażania i debugowania.

| Przełącznik wiersza polecenia | Opis |
|---------------------| - |
| `/ResetSkipPkgs` | Czyści wszystkie opcje ładowania pominąć, które zostały dodane przez użytkowników, którzy chcą uniknąć ładowania problematycznych VSPackages, a następnie uruchamia Visual Studio. Obecność SkipLoading tag wyłącza ładowanie VSPackage. Wyczyszczenie tagu ponownie umożliwia ładowanie VSPackage.<br /><br /> Ten przełącznik nie ma żadnych argumentów. |
| `/RootSuffix` | Uruchamia program Visual Studio przy użyciu alternatywnej lokalizacji. Następujące polecenie jest uruchamiane przez skrót utworzony przez instalatora zestawów SDK programu Visual Studio:<br /><br /> `devenv /RootSuffix exp`<br /><br /> W takim `exp` przypadku identyfikuje lokalizację z określonym sufiksem (na przykład `10.0Exp` zamiast ). `10.0` Eksperymentalne wystąpienie umożliwia debugowanie VSPackage oddzielnie od wystąpienia programu Visual Studio, którego używasz do pisania kodu.<br /><br /> Ten przełącznik może przyjmować dowolny ciąg identyfikujące lokalizację utworzoną przy użyciu programu VSRegEx.exe. Aby uzyskać więcej informacji, zobacz [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md). |
| `/SafeMode` | Uruchamia program Visual Studio w trybie awaryjnym, ładując tylko domyślny IDE i usługi. Przełącznik `/SafeMode` zapobiega wszystkie vspackages innych firm z ładowania po uruchomieniu programu Visual Studio, zapewniając stabilne wykonanie.<br /><br /> Ten przełącznik nie ma żadnych argumentów. |
| `/Setup` | Wymusza program Visual Studio do scalania metadanych zasobów, który opisuje menu, paski narzędzi i grupy poleceń ze wszystkich dostępnych vspackages. To polecenie można uruchomić tylko jako administrator. <br /><br /> Ten przełącznik nie ma żadnych argumentów. Polecenie `devenv /Setup` jest zazwyczaj podane jako ostatni krok procesu instalacji. Użycie przełącznika `/Setup` nie uruchamia IDE.|
| `/Splash` | Pokazuje ekran powitalny programu Visual Studio, jak zwykle, a następnie pokazuje okno komunikatu przed wyświetleniem głównego IDE. Okno komunikatu umożliwia badanie ekranu powitalnego (na przykład, aby sprawdzić ikonę produktu VSPackage).<br /><br /> Ten przełącznik nie ma żadnych argumentów. |

## <a name="see-also"></a>Zobacz też

- [Dodawanie przełączników wiersza polecenia](../extensibility/adding-command-line-switches.md)
- [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)
