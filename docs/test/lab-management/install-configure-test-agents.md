---
title: Instalowanie agentów testowych i kontrolerów testów
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27f030fb73629172e0b5a2d5d4cb27cf186bb69f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594269"
---
# <a name="install-test-agents-and-test-controllers"></a>Instalowanie agentów testowych i kontrolerów testów

W scenariuszach testowych, które używają programu Visual Studio i planów testów platformy Azure lub team foundation server (TFS), nie potrzebujesz kontrolera testów. Agenci programu Visual Studio obsługują aranżację, komunikując się z planami testów platformy Azure lub usługami TFS. Scenariusz może być uruchamianie ciągłych testów dla przepływów pracy kompilacji i wydania w planach testów platformy Azure lub TFS.

Można również rozważyć, czy lepiej jest użyć [zarządzania kompilacji lub wersji](use-build-or-rm-instead-of-lab-management.md) zamiast zarządzania laboratorium.

## <a name="system-requirements"></a>Wymagania systemowe

W poniższej tabeli przedstawiono wymagania systemowe dotyczące instalowania agenta testowego lub kontrolera testów dla programu Visual Studio:

| Element | Wymagania |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Windows Server 2016 Standard i Centrum danych<br />Windows Server 2012 R2 |
| **Kontrolera** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Windows Server 2016 Standard i Centrum danych<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Zainstaluj sterownik testowy i agentów testowych

Agenci programu Visual Studio można pobrać z [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). *Poszukaj agentów dla programu Visual Studio 2019*, wybierz *agenta* lub *kontrolera,* a następnie wybierz pozycję *Pobierz*. Uruchom pobrany plik wykonywalny, aby zainstalować agenta testowego lub kontrolera.

Agenci programu Visual Studio 2017, Visual Studio 2015 i Visual Studio 2013 można pobrać ze starszej strony [pobierania.](https://visualstudio.microsoft.com/vs/older-downloads/)

Instalatory te są dostępne jako pliki ISO dla łatwej instalacji na maszynach wirtualnych.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Zgodne wersje TFS, Microsoft Test Manager, kontrolera testów i agenta testowego

Można mieszać różne wersje TFS, Microsoft Test Manager, kontroler testów i agenta testowego, zgodnie z następującą tabelą:

| TFS | Menedżer testów firmy Microsoft z Centrum laboratorium | Kontrolera | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: uaktualnienie z 2015 r. lub nowa instalacja | 2017 | 2017 | 2017 |
| 2017: uaktualnienie z 2015 r. lub nowa instalacja | 2017 | Aktualizacja 5 z 2013 r. | Aktualizacja 5 z 2013 r. |
| 2017: uaktualnienie z 2015 r. lub nowa instalacja | 2015 | Aktualizacja 5 z 2013 r. | Aktualizacja 5 z 2013 r. |
| 2015: uaktualnienie z 2013 r. | 2013 | 2013 |2013 |
| 2015: nowa instalacja | 2013 | 2013 | 2013 |
| 2015: uaktualnienie z 2013 r. lub nowa instalacja | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

> [!NOTE]
> Scenariusze zarządzania laboratorium w TFS 2018 i usługi Azure DevOps są przestarzałe. Aby uzyskać więcej informacji, zobacz [TFS 2018 Release Notes](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Uaktualnianie z agentów testowych programu Visual Studio 2013

Zaleca się użycie agentów dla programu Visual Studio we wszystkich nowych scenariuszach automatycznego testowania. Można użyć *zadania Wdrażanie agentów testowych* w potoku kompilacji, aby pobrać i zainstalować agentów testowych na komputerze.

W poniższej tabeli przedstawiono scenariusze obsługiwane przez agentów dla programu Visual Studio 2013 oraz alternatywy dla programu Team Foundation Server (TFS) 2015 i planów testów platformy Azure:

| Scenariusze obsługiwane przez agentów programu Visual Studio 2013 | Alternatywa w planach testów TFS i Azure |
| - | - |
| Przepływ pracy Kompilacja-Wdrażanie-Test w programie Visual Studio | Użytkownicy mogą używać [potoku kompilacji](/azure/devops/pipelines/index?view=vsts) (nie kompilacji XAML) do tworzenia, wdrażania i testowania scenariuszy w TFS. |
| Testowanie obciążenia (testowanie wydajności) przy użyciu lokalnych komputerów zdalnych | Użyj kontrolera testów i agentów testowych 2013 Aktualizacja 5 do uruchamiania testów obciążenia lokalnie. |
| Zdalne wykonywanie zautomatyzowanych testów z menedżera testów firmy Microsoft przy użyciu środowiska laboratoryjnego | Obecnie nie ma alternatywy dla tego scenariusza. Zaleca się użycie zadania Uruchom testy funkcjonalne w definicjach kompilacji i wersji (nie w kompilacji XAML) do zdalnego wykonywania testów. |
| Deweloperzy wykonujący testy zdalne w programie Visual Studio | Nie są już obsługiwane. |
