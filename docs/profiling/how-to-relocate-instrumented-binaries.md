---
title: 'Instrukcje: Zmień lokalizację instrumentowanych danych binarnych | Dokumentacja firmy Microsoft'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8b50c5b76ea5b22bc9d734d32e433db1c7594d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893081"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Instrukcje: Zmienianie lokalizacji instrumentowanych danych binarnych

Podczas Instrumentacji sondy są wstawiane do plików binarnych do pomiaru wydajności aplikacji. Wybierając Zmień lokalizację instrumentowanych danych binarnych kopię oryginalny plik binarny jest Instrumentacji i umieścić w określonej lokalizacji. Ta opcja jest przydatna, jeśli nie chcesz, aby program profilujący do zmiany nazwy oryginalny plik binarny. Jeśli plik binarny nie został przeniesiony, jest zastępowany oryginalną wersję pliku binarnego.

## <a name="to-relocate-instrumented-binary"></a>Aby zmienić lokalizację instrumentowanych danych binarnych

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **właściwości**.

2. W **stron właściwości**, kliknij przycisk **binarne** właściwości.

3. Wybierz **przemieszczanie instrumentowanych plików binarny** pole wyboru.

4. Określ lokalizację dla instrumentowanego pliku binarnego.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[VSInstr](../profiling/vsinstr.md)
