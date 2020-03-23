---
title: Śledzenie plików | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 9335ca6608d36edbd17e47a441e13aecaa41c890
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634204"
---
# <a name="file-tracking"></a>Śledzenie plików

Śledzenie plików rejestruje wywołania systemu plików Systemu Windows dla procesu i jego procesów podrzędnych. Wywołując funkcje wymienione poniżej, programy kontrolują, kiedy włączyć i wyłączyć to rejestrowanie i określić plik dziennika do użycia.

- [Kontekst EndTracking](../msbuild/endtrackingcontext.md) Zatrzymaj śledzenie bieżącego kontekstu.

- [Wznawianie śledzenia](../msbuild/resumetracking.md) Wznowić śledzenie po wywołaniu [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount (Konto SetThreadCount)](../msbuild/setthreadcount.md) Ustaw liczbę wątków, które mają być używane do śledzenia.

- [Kontekst StartTracking](../msbuild/starttrackingcontext.md) Rozpocznij nowy kontekst śledzenia.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Rozpocznij nowy kontekst śledzenia z określonym katalogiem głównym.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Używane zasoby śledzenia końcowego i zwalniania.

- [Wstrzymaj śledzenie](../msbuild/suspendtracking.md) Tymczasowo zawiesić śledzenie.

- [WriteAllTLogs (WriteAllTLogs)](../msbuild/writealltlogs.md) Zapisz dzienniki śledzenia dla wszystkich kontekstów.

- [WriteContextTLogs (WriteContextTLogs)](../msbuild/writecontexttlogs.md) Zapisz dziennik śledzenia dla bieżącego kontekstu.
