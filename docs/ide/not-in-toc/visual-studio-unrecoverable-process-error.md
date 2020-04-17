---
title: W procesie wystąpił nieodwracalny błąd
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
ms.openlocfilehash: c30ac5950ca9bf775b05e9f77867c119b7c7565d
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544344"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Błąd procesu nieodwracalnego w programie Visual Studio

Visual Studio używa kilku procesów out-of-proc do uruchamiania wymaganych zadań w tle, takich jak testowanie jednostek na żywo, analizatory kodu i inne. Te procesy są uruchamiane out-of-proc dać zalety wydajności programu Visual Studio, takie jak włączenie visual studio szybciej reagować podczas uruchamiania długich, prac intensywnie korzystających z zasobów. Ponadto ponieważ visual studio jest procesem 32-bitowym, uruchamianie procesów out-of-proc daje pracy intensywnie korzystającej z pamięci większą przestrzeń pamięci, w którym do pracy.

Jeśli proces *ServiceHub.RoslynCodeAnalysisService.exe* lub *ServiceHub.RoslynCodeAnalysisService32.exe* zakończy się z jakiegoś powodu, pojawi się podręczny pasek informacji z następującym komunikatem:

**"Niestety proces używany przez program Visual Studio napotkał nieodwracalny błąd. Zalecamy zapisanie pracy, a następnie zamknięcie i ponowne uruchomienie programu Visual Studio."**

Jeśli widzisz ten komunikat, należy zapisać pracę, a następnie zamknąć i ponownie uruchomić program Visual Studio.

## <a name="list-of-processes"></a>Lista procesów

Poniżej znajduje się lista procesów out-of-proc używanych przez program Visual Studio. Ta lista obejmuje procesy uruchamiane w określonych przepływach pracy lub scenariuszach, a więc w większości przypadków nie są one uruchomione w tym samym czasie.

- Plik Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- Msbuild.exe
- Plik PerfWatson2.exe
- SkryptSandbox64.exe
- UsługaHub.Host.CLR.x86.exe
- UsługaHub.Host.Node.x86.exe
- UsługaHub.IdentityHost.exe
- UsługaHub.RoslynCodeAnalysisService.exe
- UsługaHub.RoslynCodeAnalysisService32.exe
- UsługaHub.SettingsHost.exe
- UsługaHub.VSDetouredHost.exe
- Plik VBCSCompiler.exe
- Program VsHub.exe
- vstest.discoveryengine.x86.exe
- WaAppAgent.exe
- Program WindowsAzureGuestAgent.exe
- Program WindowsAzureTelemetryService.exe

Jeśli którykolwiek z tych procesów zakończy się nieoczekiwanie, niektóre funkcje w programie Visual Studio przestaje działać. W przypadku niektórych procesów utrata funkcjonalności może być nieistotna. Dla innych, stabilność programu Visual Studio ma wpływ i wyświetlany jest komunikat o błędzie.
