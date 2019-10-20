---
title: Proces napotkał nieodwracalny błąd
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fae832cf62b2cfc6302289352bc5a2f2afb9f13
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667052"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Błąd niemożliwy do odzyskania procesu programu Visual Studio

Program Visual Studio używa kilku procesów out-of-proc do uruchamiania wymaganych zadań w tle, takich jak testy jednostkowe na żywo, analizatory kodu i nie tylko. Te procesy są uruchamiane poza procesem w celu zapewnienia korzyści z wydajności programu Visual Studio, takich jak umożliwienie programowi Visual Studio szybszej reakcji w przypadku długotrwałych zadań intensywnie korzystających z zasobów. Ponadto, ponieważ program Visual Studio jest procesem 32-bitowym, uruchamianie procesów out-of-proc zapewnia większą ilość miejsca w pamięci, w której należy pracować.

Jeśli proces *zadanie servicehub. RoslynCodeAnalysisService. exe* lub *zadanie servicehub. RoslynCodeAnalysisService32. exe* zostanie z jakiegoś powodu zakończony, pojawi się podręczny pasek informacji z następującym komunikatem:

**"Niestety, proces używany przez program Visual Studio napotkał nieodwracalny błąd. Zalecamy zapisanie pracy, a następnie zamknięcie i ponowne uruchomienie programu Visual Studio.**

Jeśli zobaczysz ten komunikat, Zapisz swoją służbę, a następnie zamknij i ponownie uruchom program Visual Studio.

## <a name="list-of-processes"></a>Lista procesów

Poniżej znajduje się lista procesów pozaprocesowych używanych przez program Visual Studio. Ta lista obejmuje procesy, które są uruchamiane w określonych przepływach pracy lub scenariuszach i dlatego w większości przypadków nie są wykonywane w tym samym czasie.

- Microsoft. Alm. Shared. Komunikacja zdalna. RemoteContainer. dll
- Microsoft. CodeAnalysis. LiveUnitTesting. EntryPoint
- Program perfwatson2. exe
- Zadanie servicehub. host. Node. x86. exe
- Zadanie servicehub. IdentityHost. exe
- Zadanie servicehub. VSDetouredHost. exe
- Zadanie servicehub. SettingsHost. exe
- Zadanie servicehub. host. CLR. x86. exe
- Zadanie servicehub. RoslynCodeAnalysisService32. exe
- Zadanie servicehub. RoslynCodeAnalysisService. exe
- WindowsAzureGuestAgent. exe
- WindowsAzureTelemetryService. exe
- WaAppAgent. exe

Jeśli którykolwiek z tych procesów zakończy się nieoczekiwanie, niektóre funkcje w programie Visual Studio przestaną działać. W przypadku niektórych procesów utrata funkcjonalności może być nieistotna. Dla innych użytkowników ma to na celu stabilność programu Visual Studio i zostanie wyświetlony komunikat o błędzie.