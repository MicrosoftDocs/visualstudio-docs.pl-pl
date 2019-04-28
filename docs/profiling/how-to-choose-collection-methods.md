---
title: 'Instrukcje: Wybieranie metod kolekcji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 344af8760dad3c66c32590b7d2d665bef833e583
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974166"
---
# <a name="how-to-choose-collection-methods"></a>Instrukcje: Wybieranie metod zbierania

Visual Studio Profiling Tools obsługują trzy metody zbieranie danych o wydajności: próbkowanie, Instrumentacja i współbieżności. Metoda próbkowania i instrumentacji umożliwia również zbieranie danych alokacji i okresie istnienia pamięci platformy .NET.

Można użyć sesji wydajności **metoda** właściwości w celu określenia najbardziej odpowiedniej metody kolekcji dla aplikacji. Metoda kolekcji można ustawić za pomocą Kreatora wydajności, Eksplorator wydajności lub ze stron właściwości sesji wydajności. Jeśli używasz narzędzia wiersza polecenia, zobacz [profilowania z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md) Aby uzyskać więcej informacji.

## <a name="performance-wizard"></a>Kreator Wydajności

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Aby wybrać metodę kolekcji za pomocą Kreatora wydajności

- Na pierwszej stronie kreatora wybierz jedną z następujących opcji:

| Opcja | Opis |
|----------------------------| - |
| **Próbkowanie Procesora** | Zbieranie statystyk aplikacji, które są przydatne do analizy początkowej i analizować problemy wykorzystanie procesora CPU. |
| **Instrumentacja** | Służy do zbierania danych o chronometrażu, które są przydatne na potrzeby ukierunkowanej analizy i analizowania problemów z wydajnością we/wy. |
| **Alokacja pamięci platformy .NET** | Gromadzi informacje o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dane alokacji pamięci za pomocą metoda profilowania próbkowanie. |
| **Współbieżność** | Zbiera dane rywalizacji o zasób liczbowych. |

## <a name="performance-explorer"></a>Eksplorator wydajności

### <a name="to-select-a-collection-method-using-performance-explorer"></a>Aby wybrać metodę kolekcji za pomocą Eksploratora wydajności

1. Na **Eksplorator wydajności** narzędzi, kliknij strzałkę obok pozycji **metoda** listy rozwijanej.

2. Kliknij metodę kolekcji, którą użytkownik sobie tego życzy.

## <a name="performance-session-property-pages"></a>Strony właściwości sesji wydajności

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Aby wybrać metodę próbkowania i instrumentacji, przy użyciu właściwości sesji wydajności

1. W **Eksplorator wydajności**, wybierz sesję wydajności.

     Zawiera nazwę pliku sesji wydajności. *psess* rozszerzenia.

2. Kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.

3. W **stron właściwości**, kliknij przycisk **ogólne**.

4. Kliknij metodę kolekcji, którą użytkownik sobie tego życzy.

    - Aby uzyskać informacje o innych opcjach, które są dostępne, gdy są zbierane dane z próbkowania, zobacz [zbieranie statystyk wydajności za pomocą próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)

    - Aby uzyskać informacje o innych opcjach, które są dostępne, gdy są zbierane dane z próbkowania, zobacz [zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Aby wybrać zbieranie danych pamięci .NET przy użyciu właściwości sesji wydajności

1. W **Eksplorator wydajności**, wybierz sesję wydajności.

     Nazwa pliku sesji wydajności ma rozszerzenie .psess.

2. Kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.

3. W **stron właściwości**, kliknij przycisk **ogólne**.

4. Kliknij przycisk **próbkowania** lub **Instrumentacji**.

5. Kliknij przycisk **informacje dotyczące alokacji obiektów .NET zbieranie** do zbierania rozmiaru i liczby [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] obiekt alokacji.

6. (Opcjonalnie) Kliknij przycisk **również zbierać informacje dotyczące okresu istnienia obiektu platformy .NET** do zbierania danych o generacje kolekcji wyrzucania elementów, w których pamięci obiektu zostało odzyskane.

     Aby uzyskać informacje o innych opcjach, które są dostępne podczas zbierania danych pamięci .NET, zobacz [.NET zbieranie danych alokacji i okresie istnienia pamięci](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Aby wybrać zbierania danych współbieżności przy użyciu właściwości sesji wydajności

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **właściwości**.

2. W **stron właściwości**, kliknij przycisk **ogólne**.

3. Kliknij przycisk **współbieżności**.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
[zrozumieć z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)
[właściwości sesji wydajności](../profiling/performance-session-properties.md)