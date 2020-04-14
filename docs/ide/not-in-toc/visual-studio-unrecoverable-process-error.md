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
ms.openlocfilehash: d1879be46498d851eec0fbfce71b2328bdfc9afb
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224443"
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
- Plik PerfWatson2.exe
- UsługaHub.Host.CLR.x86.exe
- UsługaHub.Host.Node.x86.exe
- UsługaHub.IdentityHost.exe
- UsługaHub.RoslynCodeAnalysisService.exe
- UsługaHub.RoslynCodeAnalysisService32.exe
- UsługaHub.SettingsHost.exe
- UsługaHub.VSDetouredHost.exe
- WaAppAgent.exe
- Program WindowsAzureGuestAgent.exe
- Program WindowsAzureTelemetryService.exe

Jeśli którykolwiek z tych procesów zakończy się nieoczekiwanie, niektóre funkcje w programie Visual Studio przestaje działać. W przypadku niektórych procesów utrata funkcjonalności może być nieistotna. Dla innych, stabilność programu Visual Studio ma wpływ i wyświetlany jest komunikat o błędzie.
