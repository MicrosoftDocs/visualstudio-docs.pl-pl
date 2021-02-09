---
title: Proces napotkał nieodwracalny błąd
description: Dowiedz się więcej na temat procesów, które mogą napotkać nieodwracalne błędy podczas normalnego działania programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/10/2020
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2ff53ecf1e3f3b377180fe85f972dca665b81f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909156"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Błąd niemożliwy do odzyskania procesu programu Visual Studio

Program Visual Studio używa kilku procesów out-of-proc do uruchamiania wymaganych zadań w tle, takich jak testy jednostkowe na żywo, analizatory kodu i nie tylko. Te procesy są uruchamiane poza procesem w celu zapewnienia korzyści z wydajności programu Visual Studio, takich jak umożliwienie programowi Visual Studio szybszej reakcji w przypadku długotrwałych zadań intensywnie korzystających z zasobów. Ponadto, ponieważ program Visual Studio jest procesem 32-bitowym, uruchamianie procesów out-of-proc zapewnia większą ilość miejsca w pamięci, w której należy pracować.

Jeśli proces *ServiceHub.RoslynCodeAnalysisService.exe* lub *ServiceHub.RoslynCodeAnalysisService32.exe* zostanie z jakiegoś powodu zakończony, zostanie wyświetlony podręczny pasek informacji z następującym komunikatem:

**"Niestety, proces używany przez program Visual Studio napotkał nieodwracalny błąd. Zalecamy zapisanie pracy, a następnie zamknięcie i ponowne uruchomienie programu Visual Studio.**

Jeśli zobaczysz ten komunikat, Zapisz swoją służbę, a następnie zamknij i ponownie uruchom program Visual Studio.

## <a name="list-of-processes"></a>Lista procesów

Poniżej znajduje się lista procesów pozaprocesowych używanych przez program Visual Studio. Ta lista obejmuje procesy, które są uruchamiane w określonych przepływach pracy lub scenariuszach i dlatego w większości przypadków nie są wykonywane w tym samym czasie.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft. CodeAnalysis. LiveUnitTesting. EntryPoint
- MSBuild.exe
- PerfWatson2.exe
- ScriptedSandbox64.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.VSDetouredHost.exe
- VBCSCompiler.exe
- VsHub.exe
- vstest.discoveryengine.x86.exe
- WaAppAgent.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe

Jeśli którykolwiek z tych procesów zakończy się nieoczekiwanie, niektóre funkcje w programie Visual Studio przestaną działać. W przypadku niektórych procesów utrata funkcjonalności może być nieistotna. Dla innych użytkowników ma to na celu stabilność programu Visual Studio i zostanie wyświetlony komunikat o błędzie.

> [!NOTE]
> Jeśli wystąpi problem, którego nie dotyczy ta strona, zgłoś go do nas za pomocą narzędzia [Zgłoś problem](../../ide/how-to-report-a-problem-with-visual-studio.md) , które pojawia się zarówno w Instalator programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
