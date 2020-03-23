---
title: 'Jak: Konfigurowanie redukcji szumów w widokach raportu | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ccfb9dab504bc3fa9405bb56c9fce82ed18820ac
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776335"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Jak: Konfigurowanie redukcji szumów w widokach raportu
Raporty wydajności można skonfigurować w celu redukcji szumów, ograniczając ilość danych, która jest prezentowana w widoku Drzewa wywołań i widoku Alokacja. Dzięki redukcji szumów problemy z wydajnością są bardziej widoczne. Jest to przydatne podczas analizowania raportów wydajności.

 Opcje konfiguracji redukcji szumów obejmują następujące ustawienia:

- **Przycinanie** Po przeanalizowaniu raportu widok pominie funkcje, które mieszczą się w skonfigurowanych ustawieniach wartości i progu, zgodnie z opisem w następującej procedurze przycinania. Domyślnie przycinanie jest włączone.

- **Składanie** Jeśli włączysz składanie, kolejne funkcje na ścieżce, które spełniają skonfigurowane ustawienia, zostaną scalone, zgodnie z opisem w następującej procedurze składania. Domyślnie składanie jest domyślnie włączone.

### <a name="to-configure-trimming-for-a-performance-report"></a>Aby skonfigurować przycinanie raportu wydajności

1. Gdy widok drzewa wywołań lub widok alokacji jest wyświetlany w wygenerowanym raporcie, w menu **Deweloper** kliknij polecenie **Profiler,** a następnie kliknij polecenie **Opcje redukcji szumów**.

     Zostanie wyświetlone okno dialogowe **Redukcja** szumów.

2. Aby włączyć przycinanie, wykonaj następujące czynności:

    1. Wybierz **włącz przycinanie**. Jest to ustawienie domyślne.

        > [!NOTE]
        > Jeśli redukcja szumów jest włączona, w raporcie zostanie wyświetlony pasek informacji. Aby uzyskać więcej informacji, zobacz [Widok drzewa wywołań](../profiling/call-tree-view.md) i [Widok alokacji](../profiling/dotnet-memory-allocations-view.md).

    2. Skonfiguruj ustawienie wartości przy użyciu listy rozwijanej **Wartość** i wybierając odpowiednie ustawienie.

    3. Skonfiguruj żądane ustawienie progu, wpisując wartość procentową w polu **tekstowym Próg.**

    4. Aby włączyć ostrzeżenie o redukcji szumów w wygenerowanym raporcie, wybierz **opcję Wyświetl ostrzeżenie, gdy włączona jest funkcja Redukcji szumów**. Jest to ustawienie domyślne.

3. Aby wyłączyć przycinanie, **wyczyść włącz przycinanie**.

4. Kliknij przycisk **OK**.

### <a name="to-configure-folding-for-a-performance-report"></a>Aby skonfigurować składanie dla raportu wydajności

1. W menu **Deweloper** kliknij polecenie **Profiler,** a następnie kliknij polecenie **Opcje redukcji szumów**.

     Zostanie wyświetlone okno dialogowe **Redukcja** szumów.

2. Aby włączyć składanie, wykonaj następujące czynności:

    1. Wybierz **włącz składanie**. Jest to ustawienie domyślne.

        > [!NOTE]
        > Jeśli redukcja szumów jest włączona, w raporcie zostanie wyświetlony pasek informacji. Aby uzyskać więcej informacji, zobacz [Widok drzewa wywołań](../profiling/call-tree-view.md) i [Widok alokacji](../profiling/dotnet-memory-allocations-view.md).

    2. Skonfiguruj ustawienie wartości, korzystając z listy rozwijanej **Wartość** i wybierając odpowiednie ustawienie.

    3. Skonfiguruj żądane ustawienie progu, wpisując wartość procentową w polu **tekstowym Próg.**

    4. Aby włączyć ostrzeżenie o redukcji szumów w wygenerowanym raporcie, wybierz **opcję Wyświetl ostrzeżenie, gdy włączona jest funkcja Redukcji szumów**. Jest to ustawienie domyślne.

3. Aby wyłączyć składanie, **wyczyść włącz składanie**.

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
- [Dostosowywanie widoków raportu narzędzi wydajności](../profiling/customizing-performance-tools-report-views.md)
- [Jak: Wykluczyć lub uwzględnić krótkie funkcje z oprzyrządowania](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [Widok drzewa wywołań](../profiling/call-tree-view.md)
- [Widok alokacji](../profiling/dotnet-memory-allocations-view.md)
