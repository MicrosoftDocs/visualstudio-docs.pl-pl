---
title: 'Jak: Zbieranie danych próbkowania na poziomie linii | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f64040c9180a152650de16b23276ab0e65cc9ead
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776361"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Jak: Zbieranie danych próbkowania na poziomie linii
Próbkowanie na poziomie wiersza jest zdolność profilera do określenia, gdzie w kodzie funkcji intensywnie korzystającej z procesora, takich jak funkcja, która ma wysokiej wyłączne próbki, procesor musi spędzać większość swojego czasu.

## <a name="overview"></a>Omówienie
 W przypadku próbkowania na poziomie wiersza profiler przechyła stos wywołań programu w ustalonych odstępach czasu i agreguje te wyniki. Wyniki te pokazują, jakie instrukcje procesor był wykonywany podczas pobierania próbek. Zebrane dane dotyczące próbek wyłącznych są następnie analizowane w celu zidentyfikowania wierszy kodu i wskaźnika instrukcji (IP).

 Próbkowanie na poziomie wiersza działa dla kodu zarządzanego i natywnego. Raporty wydajności, które wyświetlają te dane, obejmują widok Linie i widok Moduły.

 Informacje o rozpoczęciu/zakończeniu znaków nie są dostępne dla kodu macierzystego. W przypadku instrukcji wielowierszowych informacje o rozpoczęciu wiersza nie są dostępne dla kodu macierzystego; dostępne są tylko informacje o końcu linii.

### <a name="available-data"></a>Dostępne dane
 Dostępne dane dotyczące pobierania próbek na poziomie linii obejmują następujące informacje:

- Nazwa funkcji.

- Adres funkcji.

- Wiersze rozpoczynają -wiersz numer przykładowego kodu.

- Koniec wiersza — końcowy numer wiersza źródłowego. Zazwyczaj jest to taka sama jak dane "Początek wiersza", z wyjątkiem sytuacji, gdy instrukcja pojedynczego programu obejmuje wiele wierszy kodu źródłowego.

- Znaki zaczynają — początkowa kolumna próbki zbiorczej. Jest to zazwyczaj 0, z wyjątkiem sytuacji, gdy pojedynczy wiersz zawiera wiele instrukcji programu.

- Koniec znaku — kolumna końcowa próbki agregującej.

- ADRES IP - adres, w którym pobrano próbkę zbiorczą (tylko widok IP).

  W widoku **Moduły,** jeśli funkcja ma statystyki na poziomie linii, statystyki są zagnieżdżone w ramach każdej funkcji. Ponadto prezentowane są statystyki na poziomie IP, które są zagnieżdżone pod każdym wierszem.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Wyłączanie próbkowania na poziomie linii dla kodu zarządzanego
 Domyślnie próbkowanie na poziomie linii jest włączone. Zbieranie danych na poziomie wiersza dla kodu zarządzanego można wyłączyć za pomocą jednego z następujących poleceń:

- Przed profilowanie wpisz **VSPerfCLREnv /samplelineoff**. Dotyczy to zarówno aplikacji, jak i usług.

     — lub —

- Podczas uruchamiania aplikacji wpisz **VSPerfCmd \</lineoff inne argumenty>**.

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
