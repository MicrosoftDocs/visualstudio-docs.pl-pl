---
title: Śledzenie plików | Microsoft Docs
description: Użyj funkcji śledzenia plików MSBuild, aby rejestrować wywołania systemu plików systemu Windows dla procesu i jego procesów podrzędnych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d61c3478515f2c8fa867666e6ff4ff72a0d4e65b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877125"
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
