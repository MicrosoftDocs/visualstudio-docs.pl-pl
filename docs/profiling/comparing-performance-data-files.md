---
title: Porównywanie plików danych dotyczących wydajności | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e75a5da65343a08f0c94be27837e70f4078192d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893052"
---
# <a name="compare-performance-data-files"></a>Porównywanie plików danych dotyczących wydajności
Funkcji porównywania plików danych narzędzi profilowania można wybrać dwa pliki raportów (. *Vsp* lub. *vsps*) plików i Generowanie raportu, który przedstawia różnice, największe Regresje wydajności i ulepszeń, które wystąpiły w jednej sesji profilowania do innego.  
  
 Raport porównawczy danych plików z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools porównanie wyników analizy w jeden plik danych profilowania, aby wyniki analizy linii bazowej w innym pliku danych. Oba pliki danych należy został wygenerowany przy użyciu tej samej metody profilowania. Raport analizy porównania jest zapisywany jako. *vsps* pliku.  
  
 Widok raportu porównania przedstawia widok tabeli zmienionych danych. W tabeli przedstawiono, różnicowej lub zmiana z linii bazowej. Delta jest obliczana przez określenie różnicy starej wartości, wartość punktu odniesienia i wartość wyniku z nowego analizy.  
  
 Porównywanie danych profilera może bazować na funkcje w kodzie, moduły w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.  
  
 Profilowanie danych, który jest dostępny dla porównania zawiera informacje, które jest wyświetlane w kolumnach. Aby uzyskać definicje tych nazw kolumn, zobacz [widoki raportu wydajności](../profiling/performance-report-views.md).  
  
 Próg można ustawić do zmniejszenia szumu i odfiltrować wszystkie dane w widoku tabeli porównanie wierszy, które nie uległy zmianie o określoną wartość.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Porównywanie plików danych dotyczących wydajności](../profiling/how-to-compare-performance-data-files.md)