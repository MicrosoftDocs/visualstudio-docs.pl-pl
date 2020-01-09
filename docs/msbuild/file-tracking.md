---
title: Śledzenie plików | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ee4620e845205a936bbdf48a9872c4dec3305ea
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596037"
---
# <a name="file-tracking"></a>Śledzenie plików
Dzienniki śledzenia plików są wywołaniami systemu plików Windows dla procesu i jego procesów podrzędnych. Wywołując funkcje wymienione poniżej, programy kontrolują, kiedy należy włączyć i wyłączyć rejestrowanie i określić plik dziennika, który ma być używany.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Zatrzymaj śledzenie bieżącego kontekstu.

- [ResumeTracking](../msbuild/resumetracking.md) Wznów śledzenie po wywołaniu [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount](../msbuild/setthreadcount.md) Ustaw liczbę wątków do użycia na potrzeby śledzenia.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Rozpocznij nowy kontekst śledzenia.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Rozpocznij nowy kontekst śledzenia z określonym katalogiem głównym.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Zasoby końcowe śledzenia i wydania są używane.

- [SuspendTracking](../msbuild/suspendtracking.md) Tymczasowe Wstrzymywanie śledzenia.

- [WriteAllTLogs](../msbuild/writealltlogs.md) Zapisz dzienniki śledzenia dla wszystkich kontekstów.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) Zapisz dziennik śledzenia dla bieżącego kontekstu.
