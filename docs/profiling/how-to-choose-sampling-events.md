---
title: Jak wybrać zdarzenia próbkowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8473ca1f5829faa2a76b5560132c7aada152dc3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329283"
---
# <a name="how-to-choose-sampling-events"></a>Instrukcje: Wybieranie zdarzeń próbkowania
Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania zbiera dane dotyczące wydajności w interwale określonym jako liczba cykli procesora, które są używane w profilowanym procesie. Domyślna liczba cykli w interwale wynosi 10 000 000, czyli około 0,01 sekund na 1% GH. Można zmienić liczbę cykli w interwale i można zmienić przykładowe zdarzenie. Dostępne są następujące przykładowe zdarzenia:

- Cykle zegara — w przypadku problemów związanych z PROCESORem.

- Błędy stron — w przypadku problemów związanych z pamięcią.

- Wywołania systemowe — w przypadku problemów związanych z we/wy.

- Licznik wydajności — liczniki procesora CPU w przypadku problemów z wydajnością niskiego poziomu.

> [!IMPORTANT]
> Jeśli zbierasz dane pamięci .NET (alokacje lub okresy istnienia obiektów lub oba) przy użyciu metody próbkowania, wszystkie zdarzenia próbkowania określone przez użytkownika są ignorowane, a odpowiednie alokacje pamięci lub zdarzenia wyrzucania elementów bezużytecznych są używane do zbierania danych.

### <a name="to-select-a-sample-event"></a>Aby wybrać przykładowe zdarzenie

1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Na **stronie właściwości**kliknij właściwości **próbkowania** .

3. Z listy rozwijanej **przykład zdarzenia** wybierz przykładowe zdarzenie, którego chcesz użyć do profilowania aplikacji.

    > [!NOTE]
    > **Dostępne liczniki wydajności** są włączane tylko w przypadku wybrania **licznika wydajności** z listy rozwijanej **przykład zdarzenia** .

4. W przypadku wybrania **licznika wydajności**wybierz określony licznik procesora w obszarze dostępne kontrolki widoku drzewa **liczników wydajności** .

    - Liczniki w węźle **zdarzenia przenośne** są dostępne na wszystkich typach procesorów.

    - Liczniki w węźle **zdarzenia platformy** są specyficzne dla procesora na bieżącym komputerze i mogą być niedostępne w przypadku innych typów procesorów.

5. Po wybraniu przykładowego zdarzenia w polu tekstowym **Interwał próbkowania** zostanie wyświetlona domyślna wartość interwału próbkowania. W razie potrzeby możesz wprowadzić wartość w polu tekstowym.

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Instrukcje: wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)
- [Liczniki procesora CPU i systemu Windows](../profiling/cpu-and-windows-counters.md)
- [Omówienie wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)
- [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
