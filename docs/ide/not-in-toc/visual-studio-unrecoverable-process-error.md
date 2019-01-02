---
title: Proces napotkał nieodwracalny błąd
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: c235a55cbb5648eec0c2e1ee0632b56b1ea537ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860965"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Błąd nieodwracalny procesu programu Visual Studio

Program Visual Studio 2017 używa kilka procesów procesem do wykonania zadania w tle wymagane, takie jak testy jednostkowe na żywo, analizatory i więcej kodu. Te procesy są uruchamiane procesem zapewnienie korzyści związanych z wydajnością programu Visual Studio, takich jak włączenie programu Visual Studio do szybszego reagowania na podczas long, uruchamiania zadań intensywnie korzystających z zasobów. Ponadto ponieważ program Visual Studio jest proces 32-bitowy, uruchomione procesy-procesem zapewnia pracy o znacznym wykorzystaniu pamięci większy obszar pamięci, w którym będą wykonywane.

Jeśli *ServiceHub.RoslynCodeAnalysisService.exe* lub *ServiceHub.RoslynCodeAnalysisService32.exe* zakończeniu procesu jakiegoś powodu pasek informacji wyskakujące pojawia się następujący komunikat o błędzie:

**"Niestety, proces używany przez program Visual Studio napotkał nieodwracalny błąd. Zalecamy Zapisywanie swojej pracy, a następnie zamknięcie i ponowne uruchomienie programu Visual Studio."**

Ten komunikat jest wyświetlony, należy zapisać swoją pracę i następnie zamknij i ponownie uruchom program Visual Studio.

## <a name="list-of-processes"></a>Lista procesów

Poniżej przedstawiono listę-procesem stosowanym przez program Visual Studio. Ta lista obejmuje procesy, które są uruchamiane w określonych przepływów pracy lub scenariuszy, a więc w większości przypadków są nie są wszystkie uruchomione w tym samym czasie.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

Jeśli dowolny z tych procesów zostaje nieoczekiwanie zamknięty, niektóre funkcje programu Visual Studio przestaje działać. Dla niektórych procesów utratę funkcji mogą być nieistotne. Dla innych osób dotyczy stabilności programu Visual Studio i jest wyświetlany komunikat o błędzie.