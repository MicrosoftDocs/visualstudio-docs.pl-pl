---
title: Zbieranie danych Line-Level próbkowania | Microsoft Docs
description: Dowiedz się, jak próbkowanie na poziomie wiersza profilera może ujawnić kod, który używa dużych ilości czasu procesora. Działa z kodem zarządzanym i natywnym.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 222ba8cd5eb8e45be368d70c204a7c7c76b1a3e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886265"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Instrukcje: zbieranie danych próbkowania na poziomie wiersza
Próbkowanie na poziomie wiersza jest zdolnością profilera do określenia, gdzie w kodzie funkcji intensywnie korzystających z procesora, takiej jak funkcja, która ma duże wykluczające się próbki, procesor musi spędzać większość czasu.

## <a name="overview"></a>Omówienie
 W przypadku próbkowania na poziomie wiersza Profiler wyszukuje stos wywołań programu w ustalonych odstępach czasu i agreguje te wyniki. Wyniki te pokazują, jakie instrukcje procesor wykonał podczas wykonywania przykładów. Zebrane dane dotyczące próbek wyłącznych są następnie analizowane w celu zidentyfikowania wierszy kodu i wskaźnika instrukcji (IP).

 Próbkowanie na poziomie wiersza działa w przypadku zarządzanych, a także kodu natywnego. Raporty dotyczące wydajności, które wyświetlają te dane, obejmują widok wiersze i widok moduły.

 Informacje o początku/końcu znaku nie są dostępne dla kodu natywnego. W przypadku instrukcji wielowierszowych informacje o rozpoczęciu wiersza nie są dostępne dla kodu natywnego; dostępne są tylko informacje o końcu wiersza.

### <a name="available-data"></a>Dostępne dane
 Dostępne dane próbkowania na poziomie wiersza zawierają następujące informacje:

- Nazwa funkcji.

- Adres funkcji.

- Początek linii numer wiersza kodu próbki.

- Linia końcowa — końcowy numer wiersza źródłowego. Jest to zazwyczaj takie samo jak dane "początek wiersza" z wyjątkiem przypadków, gdy instrukcja pojedynczego programu obejmuje wiele wierszy kodu źródłowego.

- Początkowa liczba znaków w kolumnie przykładu agregacji. Zwykle jest to wartość 0, chyba że pojedynczy wiersz zawiera wiele instrukcji programu.

- Koniec znaku — kolumna końcowa próbki agregowanej.

- Adres IP, na którym wykonano próbkę agregowania (tylko widok IP).

  W widoku **moduły** , jeśli funkcja ma statystyki na poziomie wiersza, statystyki są zagnieżdżone w każdej funkcji. Ponadto są prezentowane statystyki na poziomie protokołu IP, które są zagnieżdżone w poszczególnych wierszach.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Wyłącz próbkowanie na poziomie wiersza dla kodu zarządzanego
 Domyślnie próbkowanie na poziomie wiersza jest włączone. Można wyłączyć zbieranie danych na poziomie wiersza dla kodu zarządzanego przy użyciu jednego z następujących poleceń:

- Przed przeprowadzeniem profilowania wpisz **VSPerfCLREnv/samplelineoff**. Dotyczy to zarówno aplikacji, jak i usług.

     oraz

- Podczas uruchamiania aplikacji wpisz **VSPerfCmd/LineOff \<other arguments>**.

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
