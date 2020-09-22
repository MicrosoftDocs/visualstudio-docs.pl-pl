---
title: Zmień lokalizację plików binarnych instrumentacji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 13fa5c3413e620e43a695e205a0523dce23e90b4
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851349"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Instrukcje: Zmienianie położenia plików binarnych z instrumentacją

Podczas Instrumentacji sondy są wstawiane do pliku binarnego w celu zmierzenia wydajności aplikacji. Po wybraniu przeniesienia pliku binarnego z instrumentacją kopia oryginalnego pliku binarnego zostaje przyprowadzona i umieszczona w określonej lokalizacji. Ta opcja jest przydatna, jeśli nie chcesz, aby Profiler zmienił nazwę oryginalnego pliku binarnego. Jeśli plik binarny nie zostanie przeniesiony, oryginalna wersja pliku binarnego zostanie nadpisywana.

## <a name="to-relocate-instrumented-binary"></a>Aby przenieść plik binarny z instrumentacją

1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Na **stronie właściwości**kliknij właściwości **binarne** .

3. Zaznacz pole wyboru **Przenieś instrumentację plików binarnych** .

4. Określ lokalizację pliku binarnego Instrumentacji.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md) 
 [VSInstr](../profiling/vsinstr.md)
