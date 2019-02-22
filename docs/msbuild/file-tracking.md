---
title: Śledzenie plików | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7770da734143b2b6185b266137eeb46ba25bd32a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640613"
---
# <a name="file-tracking"></a>Śledzenie plików
Śledzenie pliku rejestruje wywołania do Windows systemu plików dla procesu i jego procesów podrzędnych. Przez wywołanie funkcji wymienionych poniżej, programy kontrolują kiedy należy włączyć rejestrowanie i wyłączyć i określ plik dziennika do użycia.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Zatrzymaj śledzenie bieżącego kontekstu.

- [ResumeTracking](../msbuild/resumetracking.md) Wznów śledzenie po wywołaniu [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount](../msbuild/setthreadcount.md) Ustaw liczbę wątków używanych na potrzeby śledzenia.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Rozpocznij nowy kontekst śledzenia.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Rozpocznij nowy kontekst śledzenia z określonym katalogiem głównym.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) zakończenia śledzenia i zwalnia zasoby używane.

- [SuspendTracking](../msbuild/suspendtracking.md) czasowo zawieszają śledzenie.

- [WriteAllTLogs](../msbuild/writealltlogs.md) zapisać dziennik śledzenia dla wszystkich kontekstów.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) zapisać dziennik śledzenia dla bieżącego kontekstu.