---
title: 'Instrukcje: Zbieranie danych pobierania próbek na poziomie wiersza | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65890bf31a1257c3a41bc1fd7ed3f732c50eda14
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068109"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Instrukcje: Zbieranie danych pobierania próbek na poziomie wiersza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Próbkowanie na poziomie wiersza jest możliwość określenia, gdzie w kodzie funkcji obciążającą procesor, takich jak funkcja, która ma wysoką wyłącznych próbek, procesor musi spędzają większość czasu profilera.  
  
## <a name="overview"></a>Omówienie  
 Pobierania próbek na poziomie wiersza, program profilujący przedstawia stos wywołań programu w ustalonych odstępach czasu i agreguje tych wyników. Te wyniki wskazują, jakie instrukcje procesor był wykonywany, gdy zostały pobrane próbki. Zebrane dane dotyczące próbek wyłącznych są następnie analizowane w celu identyfikacji wierszy kodu i wskaźnik instrukcji (IP).  
  
 Próbkowanie na poziomie wiersza działa dla kodu zarządzanego, jak również natywnych. Raporty dotyczące wydajności, które wyświetlają dane te obejmują widok wierszy i widok modułów.  
  
 Informacje o znaku rozpoczęcia/zakończenia nie jest dostępne dla kodu natywnego. Dla instrukcji wielowierszowego wiersz rozpocząć informacji jest niedostępna dla kodu natywnego; dostępne są tylko informacje zakończenia wiersza.  
  
### <a name="available-data"></a>Dostępne dane  
 Dane dostępne próbkowania na poziomie wiersza zawiera następujące informacje:  
  
- Nazwa funkcji.  
  
- Adres funkcji.  
  
- Rozpocznij wiersz — numer wiersza, próbki kodu.  
  
- Wiersz i zakończenia — numer wiersza źródła. Ogólnie jest taka sama jak "Początek wiersza" danych, z wyjątkiem sytuacji, gdy pojedynczej instrukcji program obejmuje kilka wierszy kodu źródłowego.  
  
- Rozpocznij znak — kolumnę początku próbka. Zwykle jest to 0, z wyjątkiem sytuacji, gdy jeden wiersz zawiera wiele instrukcji programu.  
  
- Znak zakończenia — kolumny próbka.  
  
- Adres IP — adres, w której próbka została wykonana (tylko w widoku adresów IP).  
  
  W **modułów** wyświetlić, jeśli funkcja statystyki na poziomie wiersza, statystyki są zagnieżdżone w każdej funkcji. Ponadto przedstawiono statystyki na poziomie adresów IP, które zostały zagnieżdżone w każdym wierszu.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Wyłącz próbkowanie poziomie wiersza dla kodu zarządzanego  
 Próbkowanie na poziomie wiersza jest domyślnie włączona. Można wyłączyć zbieranie danych na poziomie wiersza dla kodu zarządzanego, wykonując jedną z następujących czynności:  
  
- Przed rozpoczęciem profilowania, wpisz **VSPerfCLREnv /samplelineoff**. Dotyczy to zarówno aplikacji i usług.  
  
     — lub —  
  
- Podczas uruchamiania aplikacji, wpisz **VSPerfCmd/lineoff \<inne argumenty >**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
