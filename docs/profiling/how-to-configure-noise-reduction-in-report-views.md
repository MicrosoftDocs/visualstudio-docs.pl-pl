---
title: 'Instrukcje: Konfigurowanie redukcji szumu w widokach raportu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99a844bbc32b3b974469fea832aaaebdcefb24f9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046581"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Instrukcje: Konfigurowanie redukcji szumu w widoku raportu
Raporty dotyczące wydajności można skonfigurować dla obniżenia poziomu hałasu, ograniczając ilość danych, które są prezentowane w widokach drzewo wywołań i alokacji. Za pomocą redukcji szumu, problemy z wydajnością są lepiej widoczne. Jest to przydatne podczas analizowania raportów wydajności.

 Opcje konfiguracji redukcji szumów obejmują następujące ustawienia:

- **Przycinanie** podczas analizy raportu widoku zostaną pominięte funkcje, które mieszczą się w ustawieniach wartości i wartości progowej, które zostały skonfigurowane, zgodnie z opisem w poniższej procedurze przycinania. Domyślnie przycinania jest włączona.

- **Składanie** po włączeniu składania, kolejnych funkcji w ścieżce, zgodne z ustawieniami, które zostały skonfigurowane zostaną scalone, zgodnie z opisem w składania opisanej poniżej procedury. Domyślnie składania jest domyślnie włączone.

### <a name="to-configure-trimming-for-a-performance-report"></a>Aby skonfigurować przycinania dla raportu dotyczącego wydajności

1. Gdy widok drzewa wywołania lub Widok alokacji jest wyświetlana w wygenerowanym raporcie na **Developer** menu, kliknij przycisk **Profiler** a następnie kliknij przycisk **opcje redukcji szumów**.

     **Obniżenia poziomu hałasu** pojawi się okno dialogowe.

2. Aby włączyć przycinanie, wykonaj następujące kroki:

    1. Wybierz **Włącz przycinanie**. To jest ustawienie domyślne.

        > [!NOTE]
        >  Jeśli włączono redukcję szumów pasek informacji będą wyświetlane w raporcie. Aby uzyskać więcej informacji, zobacz [widok drzewa wywołań](../profiling/call-tree-view.md) i [Widok alokacji](../profiling/dotnet-memory-allocations-view.md).

    2. Skonfiguruj ustawienie wartości przy użyciu **wartość** listy rozwijanej i wybierając odpowiednie ustawienie.

    3. Skonfiguruj ustawienie żądaną wartość progową, wpisując wartość procentową w **próg** pola tekstowego.

    4. Aby włączyć ostrzeżenie redukcji szumu w generowanym raporcie, zaznacz **wyświetlania ostrzeżenia, gdy redukcja szumów jest włączona**. To jest ustawienie domyślne.

3. Aby wyłączyć przycinania, czyszczenia **Włącz przycinanie**.

4. Kliknij przycisk **OK**.

### <a name="to-configure-folding-for-a-performance-report"></a>Aby skonfigurować składanie raportu wydajności

1. Na **Developer** menu, kliknij przycisk **Profiler** a następnie kliknij przycisk **opcje redukcji szumów**.

     **Obniżenia poziomu hałasu** pojawi się okno dialogowe.

2. Aby umożliwić składanie, wykonaj następujące kroki:

    1. Wybierz **Włącz zwijanie**. To jest ustawienie domyślne.

        > [!NOTE]
        >  Jeśli włączono redukcję szumów pasek informacji będą wyświetlane w raporcie. Aby uzyskać więcej informacji, zobacz [widok drzewa wywołań](../profiling/call-tree-view.md) i [Widok alokacji](../profiling/dotnet-memory-allocations-view.md).

    2. Skonfiguruj ustawienie wartości przy użyciu **wartość** listy rozwijanej i wybierając odpowiednie ustawienie.

    3. Skonfiguruj ustawienie żądaną wartość progową, wpisując wartość procentową w **próg** pola tekstowego.

    4. Aby włączyć ostrzeżenie redukcji szumu w generowanym raporcie, zaznacz **wyświetlania ostrzeżenia, gdy redukcja szumów jest włączona**. To jest ustawienie domyślne.

3. Aby wyłączyć, zwijanie, wyczyść **Włącz składanie**.

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także
- [Dostosowywanie widoków raportów narzędzi wydajności](../profiling/customizing-performance-tools-report-views.md)
- [Instrukcje: Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [Widok drzewa wywołań](../profiling/call-tree-view.md)
- [Widok alokacji](../profiling/dotnet-memory-allocations-view.md)