---
title: Instalowanie agentów testowych i kontrolerów testów
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edb10246437bff9bef0a6f76ffde95bc12855944
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653080"
---
# <a name="install-test-agents-and-test-controllers"></a>Instalowanie agentów testowych i kontrolerów testów

W przypadku scenariuszy testowych, które korzystają z programu Visual Studio i Azure Test Plans lub Team Foundation Server (TFS), nie jest potrzebny kontroler testów. Agenci programu Visual Studio obsługują aranżację, komunikując się z Azure Test Plans lub TFS. Scenariuszem może być uruchomienie testów ciągłych dla przepływów pracy kompilowania i wydawania w Azure Test Plans lub TFS.

Warto również rozważyć, czy lepiej jest używać programu [Build lub Release Management](use-build-or-rm-instead-of-lab-management.md) zamiast Lab Management.

## <a name="system-requirements"></a>Wymagania systemowe

W poniższej tabeli przedstawiono wymagania systemowe dotyczące instalowania agenta testowego lub kontrolera testów dla programu Visual Studio:

| Element | Wymagania |
| ---- | ------------ |
| **Odczynnik** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Windows Server 2016 Standard i Datacenter<br />Windows Server 2012 z dodatkiem R2 |
| **Kontroler** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 z dodatkiem Service Pack 1<br />Windows Server 2016 Standard i Datacenter<br />Windows Server 2012 z dodatkiem R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Instalowanie kontrolera testów i agentów testowych

Agentów programu Visual Studio można pobrać z [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Wyszukaj *agentów dla programu Visual Studio 2019*, wybierz opcję *Agent* lub *kontroler*, a następnie wybierz pozycję *Pobierz*. Uruchom pobrany plik wykonywalny, aby zainstalować agenta testowego lub kontrolera.

Możesz pobrać agentów dla programu Visual Studio 2017, Visual Studio 2015 i Visual Studio 2013 ze [starszej strony pobierania](https://visualstudio.microsoft.com/vs/older-downloads/) .

Te Instalatory są dostępne jako pliki ISO do prostej instalacji na maszynach wirtualnych.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Zgodne wersje serwera TFS, Microsoft Test Manager, kontrolera testów i agenta testowego

Można mieszać różne wersje TFS, Microsoft Test Manager, kontrolera testów i agenta testowego, zgodnie z poniższą tabelą:

| TFS | Microsoft Test Manager z Centrum laboratoryjnym | Kontroler | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: Uaktualnij program 2015 lub nową instalację | 2017 | 2017 | 2017 |
| 2017: Uaktualnij program 2015 lub nową instalację | 2017 | 2013 Update 5 | 2013 Update 5 |
| 2017: Uaktualnij program 2015 lub nową instalację | 2015 | 2013 Update 5 | 2013 Update 5 |
| 2015: Uaktualnianie z 2013 | 2013 | 2013 |2013 |
| 2015: Nowa instalacja | 2013 | 2013 | 2013 |
| 2015: Uaktualnij program 2013 lub nową instalację | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

> [!NOTE]
> Scenariusze zarządzania laboratorium w programie TFS 2018 i Azure DevOps Services są przestarzałe. Aby uzyskać więcej informacji, zobacz [Informacje o wersji programu TFS 2018](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Uaktualnianie z Visual Studio 2013 agentów testowych

Zalecamy korzystanie z agentów programu Visual Studio we wszystkich nowych scenariuszach zautomatyzowanych testów. Możesz użyć zadania *Wdróż agentów testowych* w potoku kompilacji, aby pobrać i zainstalować agentów testowych na komputerze.

W poniższej tabeli przedstawiono scenariusze obsługiwane przez agentów dla Visual Studio 2013 i alternatywy dla Team Foundation Server (TFS) 2015 i Azure Test Plans:

| Scenariusze obsługiwane przez agentów dla Visual Studio 2013 | Alternatywa w programie TFS i Azure Test Plans |
| - | - |
| Przepływ pracy Kompilacja-Wdrażanie-test w programie Visual Studio | Użytkownicy mogą korzystać z [potoku kompilacji](/azure/devops/pipelines/index?view=vsts) (nie kompilacja XAML) dla scenariuszy kompilowania, wdrażania i testowania w programie TFS. |
| Testowanie obciążenia (testowanie wydajności) przy użyciu lokalnych maszyn zdalnych | Użyj Test Controller i przetestuj Agents 2013 Update 5, aby uruchomić testy obciążenia lokalnie. |
| Zdalne wykonywanie testów automatycznych z Microsoft Test Manager przy użyciu środowiska laboratoryjnego | Obecnie nie ma żadnych alternatyw dla tego scenariusza. Zalecamy używanie zadania Uruchom testy funkcjonalne w definicjach kompilacji i wydania (nie w kompilacji XAML) do zdalnego wykonywania testów. |
| Deweloperzy wykonujący testy zdalne w programie Visual Studio | Nie jest już obsługiwane. |
