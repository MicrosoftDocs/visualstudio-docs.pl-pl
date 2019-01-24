---
title: Porównywanie plików danych dotyczących wydajności | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 132a3cb5f7d4257aa0728960cb5bfd50c5ee3066
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763205"
---
# <a name="comparing-performance-data-files"></a>Porównywanie plików danych dotyczących wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcji porównywania plików danych narzędzi profilowania można wybrać dwa pliki raportów (. VSP lub. VSPS), pliki i Generowanie raportu, który przedstawia różnice, największe Regresje wydajności i ulepszeń, które wystąpiły w jednej sesji profilowania do innego.  
  
 Raport porównawczy danych plików z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools porównanie wyników analizy w jeden plik danych profilowania, aby wyniki analizy linii bazowej w innym pliku danych. Oba pliki danych należy został wygenerowany przy użyciu tej samej metody profilowania. Raport analizy porównania jest zapisywany jako plik .vsps.  
  
 Widok raportu porównania przedstawia widok tabeli zmienionych danych. W tabeli przedstawiono, różnicowej lub zmiana z linii bazowej. Delta jest obliczana przez określenie różnicy starej wartości, wartość punktu odniesienia i wartość wyniku z nowego analizy.  
  
 Porównywanie danych profilera może bazować na funkcje w kodzie, moduły w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.  
  
 Profilowanie danych, który jest dostępny dla porównania zawiera informacje, które jest wyświetlane w kolumnach. Aby uzyskać definicje tych nazw kolumn, zobacz [widoki raportu wydajności](../profiling/performance-report-views.md).  
  
 Próg można ustawić do zmniejszenia szumu i odfiltrować wszystkie dane w widoku tabeli porównanie wierszy, które nie uległy zmianie o określoną wartość.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Porównywanie plików danych wydajności](../profiling/how-to-compare-performance-data-files.md)
