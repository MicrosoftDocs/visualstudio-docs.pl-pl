---
title: 'Jak: Przeniesienie instrumentowanych plików binarnych | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cddbb0b3e27b841441937b7256ea32d722e25f5e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774903"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Jak: Przenoszenie instrumentowanych plików binarnych

Podczas oprzyrządowania sondy są wstawiane do pliku binarnego w celu pomiaru wydajności aplikacji. Decydując się na przeniesienie instrumentowanego pliku binarnego, kopia oryginalnego pliku binarnego jest instrumentowana i umieszczana w określonej lokalizacji. Ta opcja jest przydatna, jeśli nie chcesz, aby profiler zmienić nazwę oryginalnego pliku binarnego. Jeśli plik binarny nie zostanie przeniesiony, oryginalna wersja pliku binarnego zostanie zastąpiona.

## <a name="to-relocate-instrumented-binary"></a>Aby przenieść instrumentowane binarne

1. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Na **stronach właściwości**kliknij właściwości **Binarne.**

3. Zaznacz pole wyboru **Przenoszenie instrumentowanych plików binarnych.**

4. Określ lokalizację dla instrumentowanego pliku binarnego.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji](../profiling/configuring-performance-sessions.md)
wydajności[VSInstr](../profiling/vsinstr.md)
