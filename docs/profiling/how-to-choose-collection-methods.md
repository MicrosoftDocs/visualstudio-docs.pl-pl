---
title: 'Jak: Wybierz metody zbierania | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3c633e12b2e0bf157ffd94ef06a5898fdc3ec830
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776348"
---
# <a name="how-to-choose-collection-methods"></a>Jak: Wybierz metody zbierania

Narzędzia profilowania programu Visual Studio obsługują trzy metody zbierania danych o wydajności: próbkowanie, instrumentacji i współbieżności. Można również użyć metody próbkowania lub instrumentacji do zbierania alokacji pamięci .NET i danych okresu istnienia.

Można użyć właściwości **Method** sesji wydajności, aby określić najbardziej odpowiednią metodę zbierania dla aplikacji. Metodę kolekcji można ustawić z Kreatora wydajności, Eksploratora wydajności lub ze stron właściwości sesji wydajności. Jeśli używasz narzędzi wiersza polecenia, zobacz [Profilowanie z wiersza polecenia, aby](../profiling/using-the-profiling-tools-from-the-command-line.md) uzyskać więcej informacji.

## <a name="performance-wizard"></a>Kreator Wydajności

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Aby wybrać metodę zbierania za pomocą Kreatora wydajności

- Na pierwszej stronie kreatora wybierz jedną z następujących opcji:

| Opcja | Opis |
|----------------------------| - |
| **Próbkowanie procesora** | Zbiera statystyki aplikacji, które są przydatne do wstępnej analizy i analizowania problemów z wykorzystaniem procesora CPU. |
| **Instrumentacji** | Zbiera szczegółowe dane chronometrażu, które są przydatne do analizy skoncentrowane i do analizowania problemów z wydajnością wejścia/wyjścia. |
| **Alokacja pamięci .NET** | Zbiera dane alokacji pamięci programu .NET Framework przy użyciu metody profilowania próbkowania. |
| **Współbieżność** | Zbiera dane rywalizacji o zasoby numeryczne. |

## <a name="performance-explorer"></a>Eksplorator wydajności

### <a name="to-select-a-collection-method-using-performance-explorer"></a>Aby wybrać metodę zbierania przy użyciu Eksploratora wydajności

1. Na pasku **narzędzi Eksploratora wydajności** kliknij strzałkę obok listy rozwijanej **Metoda.**

2. Kliknij preferowaną metodę zbierania.

## <a name="performance-session-property-pages"></a>Strony właściwości sesji wydajności

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Aby wybrać metodę próbkowania lub instrumentacji przy użyciu właściwości sesji wydajności

1. W **Eksploratorze wydajności**wybierz sesję wydajności.

     Nazwa pliku sesji wydajności ma plik . *psess* rozszerzenie.

2. Kliknij prawym przyciskiem myszy sesję skuteczności, a następnie kliknij polecenie **Właściwości**.

3. Na **stronach właściwości**kliknij pozycję **Ogólne**.

4. Kliknij preferowaną metodę zbierania.

    - Aby uzyskać informacje o innych opcjach dostępnych podczas zbierania danych próbkowania, zobacz [Zbieranie statystyk wydajności przy użyciu próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)

    - Aby uzyskać informacje o innych opcjach dostępnych podczas zbierania danych próbkowania, zobacz [Zbieranie szczegółowych danych chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Aby wybrać zbieranie danych pamięci .NET przy użyciu właściwości sesji wydajności

1. W **Eksploratorze wydajności**wybierz sesję wydajności.

     Nazwa pliku sesji wydajności ma rozszerzenie psess.

2. Kliknij prawym przyciskiem myszy sesję skuteczności, a następnie kliknij polecenie **Właściwości**.

3. Na **stronach właściwości**kliknij pozycję **Ogólne**.

4. Kliknij **pozycję Próbkowanie** lub **Instrumentacja**.

5. Kliknij **pozycję Zbierz informacje o alokacji obiektów .NET,** aby zebrać rozmiar i liczbę alokacji obiektów programu .NET Framework.

6. (Opcjonalnie) Kliknij **również zbierać informacje o okresie istnienia obiektu .NET,** aby zbierać dane o generacjach wyrzucania elementów bezużytecznych, w których pamięć obiektu została odzyskana.

     Aby uzyskać informacje o innych opcjach dostępnych podczas zbierania danych pamięci .NET, zobacz [Zbieranie danych dotyczących alokacji pamięci .NET i okresu istnienia .](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Aby wybrać zbieranie danych współbieżności przy użyciu właściwości sesji wydajności

1. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Na **stronach właściwości**kliknij pozycję **Ogólne**.

3. Kliknij **pozycję Współbieżność**.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji](../profiling/configuring-performance-sessions.md)
wydajności Zrozumienie wartości
[danych próbkowania](../profiling/understanding-sampling-data-values.md)[Właściwości sesji wydajności](../profiling/performance-session-properties.md)
