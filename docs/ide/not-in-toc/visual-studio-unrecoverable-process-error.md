---
title: Proces napotkał nieodwracalny błąd
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 206fcddca51f8e770e013ff67de6ae3d5562f633
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585798"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Błąd niemożliwy do odzyskania procesu programu Visual Studio

Program Visual Studio używa kilku procesów out-of-proc do uruchamiania wymaganych zadań w tle, takich jak testy jednostkowe na żywo, analizatory kodu i nie tylko. Te procesy są uruchamiane poza procesem w celu zapewnienia korzyści z wydajności programu Visual Studio, takich jak umożliwienie programowi Visual Studio szybszej reakcji w przypadku długotrwałych zadań intensywnie korzystających z zasobów. Ponadto, ponieważ program Visual Studio jest procesem 32-bitowym, uruchamianie procesów out-of-proc zapewnia większą ilość miejsca w pamięci, w której należy pracować.

Jeśli proces *zadanie servicehub. RoslynCodeAnalysisService. exe* lub *zadanie servicehub. RoslynCodeAnalysisService32. exe* zostanie z jakiegoś powodu zakończony, pojawi się podręczny pasek informacji z następującym komunikatem:

**"Niestety, proces używany przez program Visual Studio napotkał nieodwracalny błąd. Zalecamy zapisanie pracy, a następnie zamknięcie i ponowne uruchomienie programu Visual Studio.**

Jeśli zobaczysz ten komunikat, Zapisz swoją służbę, a następnie zamknij i ponownie uruchom program Visual Studio.

## <a name="list-of-processes"></a>Lista procesów

Poniżej znajduje się lista procesów pozaprocesowych używanych przez program Visual Studio. Ta lista obejmuje procesy, które są uruchamiane w określonych przepływach pracy lub scenariuszach i dlatego w większości przypadków nie są wykonywane w tym samym czasie.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- Program perfwatson2. exe
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

Jeśli którykolwiek z tych procesów zakończy się nieoczekiwanie, niektóre funkcje w programie Visual Studio przestaną działać. W przypadku niektórych procesów utrata funkcjonalności może być nieistotna. Dla innych użytkowników ma to na celu stabilność programu Visual Studio i zostanie wyświetlony komunikat o błędzie.
