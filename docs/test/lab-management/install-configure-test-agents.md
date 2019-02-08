---
title: Instalowanie agentów testowych i kontrolerów testów
ms.date: 10/24/2018
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55cff84a4633b3b59d8167c0f460cbd96a98f04c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912745"
---
# <a name="install-test-agents-and-test-controllers"></a>Instalowanie agentów testowych i kontrolerów testów

Do obsługi scenariuszy testowych, które używają programu Visual Studio i plany testów platformy Azure lub Team Foundation Server (TFS) nie jest potrzebny kontroler testów. Agents for Visual Studio obsługiwać aranżację, komunikując się z planów testowych platformy Azure lub na serwerze TFS. Scenariusz można uruchomić testy ciągłej kompilacji, a następnie zwolnij przepływów pracy w programie planów testowych platformy Azure lub na serwerze TFS.

Możesz też rozważyć, czy jest lepiej używać [kompilacji lub release management](use-build-or-rm-instead-of-lab-management.md) zamiast na zarządzaniu laboratorium.

## <a name="system-requirements"></a>Wymagania systemowe

W poniższej tabeli przedstawiono wymagania systemowe dotyczące instalowania kontrolera testów agent lub test programu Visual Studio 2017:

| Element | Wymagania |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Windows Server 2016 Standard i Datacenter<br />Windows Server 2012 z dodatkiem R2 |
| **Controller** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Windows Server 2016 Standard i Datacenter<br />Windows Server 2012 z dodatkiem R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Zainstaluj agentów testowych i kontrolera testów

Możesz pobrać agents for Visual Studio 2017 z [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Wyszukaj *Agents for Visual Studio 2017*, wybierz opcję *agenta* lub *kontrolera*, a następnie wybierz *Pobierz*. Uruchom pobrany plik wykonywalny, aby zainstalować agenta testowego lub kontrolera.

Możesz pobrać agenci dla programu Visual Studio 2015 i Visual Studio 2013 ze [starsze pliki do pobrania](https://visualstudio.microsoft.com/vs/older-downloads/) strony.

Te instalatory są dostępne jako pliki ISO w celu łatwej instalacji na maszynach wirtualnych.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Zgodne wersje serwera TFS, Microsoft Test Manager, kontroler testów i agenta testowego

Można łączyć różne wersje programu TFS, Microsoft Test Manager, kontroler testów i agenta testowego, zgodnie z poniższą tabelą:

| TFS | Program Microsoft Test Manager przy użyciu Centrum laboratoryjnego | Kontroler | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: instalacji lub uaktualniania z dnia 2015 | 2017 | 2017 | 2017 |
| 2017: instalacji lub uaktualniania z dnia 2015 | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017: instalacji lub uaktualniania z dnia 2015 | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015: uaktualnianie z 2013 | 2013 | 2013 |2013 |
| 2015: nowej instalacji | 2013 | 2013 | 2013 |
| 2015: uaktualnianie z 2013, jak i nowej instalacji | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

> [!NOTE]
> Scenariusze zarządzania laboratorium w serwerze TFS 2018 i usługom DevOps platformy Azure są przestarzałe. Aby uzyskać więcej informacji, zobacz [informacje o wersji programu TFS 2018](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Uaktualnienie z agentów testowych programu Visual Studio 2013

Firma Microsoft zaleca użycie agentów programu Visual Studio, we wszystkich nowych scenariuszach testów automatycznych. Możesz użyć *wdrażanie agenci testowi* zadań w potoku kompilacji, aby pobrać i zainstalować agentów testowych na maszynie.

W poniższej tabeli przedstawiono scenariusze obsługiwane przez agentów dla programu Visual Studio 2013 i alternatyw dla Team Foundation Server (TFS) 2015 i planów testowych platformy Azure:

| Scenariusze obsługiwane przez agentów programu Visual Studio 2013 | Alternatywnie TFS i planów testowych platformy Azure |
| - | - |
| Przepływ pracy kompilacja-wdrożenie-Test, w programie Visual Studio | Użytkownicy mogą używać [tworzenie potoku](/azure/devops/pipelines/index?view=vsts) (nie kompilacja XAML) dla kompilacji, wdrażania oraz testowania scenariuszy w programie TFS. |
| Obciążenia testowania (testowanie wydajności) za pomocą polecenia zdalnego maszyn lokalnych | Użyj kontrolera testów i Test Agents 2013 Update 5 do uruchomienia obciążenia testy w środowisku lokalnym. |
| Zdalne wykonywanie zautomatyzowanych testów z Microsoft Test Manager za pomocą środowiska laboratoryjnego | Obecnie nie ma żadnej alternatywy dla tego scenariusza. Firma Microsoft zaleca używanie zadanie Uruchom testy funkcjonalne w kompilacji i definicje wersji (nie w usłudze kompilacji XAML) do wykonywania testów zdalnie. |
| Deweloperom wykonywanie testów zdalnego w programie Visual Studio | Nie jest już obsługiwana. |
