---
title: 'Instrukcje: Zbieranie danych pobierania próbek na poziomie wiersza | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e447b0b15a7a541567932a72dffd7abfc9851e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834591"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Instrukcje: Zbieranie danych pobierania próbek na poziomie wiersza
Próbkowanie na poziomie wiersza jest możliwość określenia, gdzie w kodzie funkcji obciążającą procesor, takich jak funkcja, która ma wysoką wyłącznych próbek, procesor musi spędzają większość czasu profilera.

## <a name="overview"></a>Omówienie
 Pobierania próbek na poziomie wiersza, program profilujący przedstawia stos wywołań programu w ustalonych odstępach czasu i agreguje tych wyników. Te wyniki wskazują, jakie instrukcje procesor był wykonywany, gdy zostały pobrane próbki. Zebrane dane dotyczące próbek wyłącznych są następnie analizowane w celu identyfikacji wierszy kodu i wskaźnik instrukcji (IP).

 Próbkowanie na poziomie wiersza działa dla kodu zarządzanego, jak również natywnych. Raporty dotyczące wydajności, które wyświetlają dane te obejmują widok wierszy i widok modułów.

 Informacje o znaku rozpoczęcia/zakończenia nie jest dostępne dla kodu natywnego. Dla instrukcji wielowierszowego wiersz rozpocząć informacji jest niedostępna dla kodu natywnego; dostępne są tylko informacje zakończenia wiersza.

### <a name="available-data"></a>Dostępne dane
 Dane dostępne próbkowania na poziomie wiersza zawiera następujące informacje:

- Nazwa funkcji.

- Adres funkcji.

- Rozpocznij wiersze — numer wiersza, próbki kodu.

- Koniec linii — końcowy numer wiersza źródła. Ogólnie jest taka sama jak "Początek wiersza" danych, z wyjątkiem sytuacji, gdy pojedynczej instrukcji program obejmuje kilka wierszy kodu źródłowego.

- Rozpocznij znaków — kolumnę początku próbka. Zwykle jest to 0, z wyjątkiem sytuacji, gdy jeden wiersz zawiera wiele instrukcji programu.

- Końcowy znak — w końcowej kolumny próbka.

- Adres IP — adres, w której próbka została wykonana (tylko w widoku adresów IP).

  W **modułów** wyświetlić, jeśli funkcja statystyki na poziomie wiersza, statystyki są zagnieżdżone w każdej funkcji. Ponadto przedstawiono statystyki na poziomie adresów IP, które zostały zagnieżdżone w każdym wierszu.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Wyłącz próbkowanie poziomie wiersza dla kodu zarządzanego
 Próbkowanie na poziomie wiersza jest domyślnie włączona. Można wyłączyć zbieranie danych na poziomie wiersza dla kodu zarządzanego przy użyciu jednej z następujących poleceń:

- Przed rozpoczęciem profilowania, wpisz **VSPerfCLREnv /samplelineoff**. Dotyczy to zarówno aplikacji i usług.

     — lub —

- Podczas uruchamiania aplikacji, wpisz **VSPerfCmd/lineoff \<inne argumenty >**.

## <a name="see-also"></a>Zobacz także
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)