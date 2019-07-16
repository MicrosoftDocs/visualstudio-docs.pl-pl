---
title: 'DA0013: Wykorzystanie funkcji String.Split i String.Substring | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6ff05e7e8cc74eacb00b5ec8ff42bd48faaa12c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159193"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Znaczące wykorzystanie funkcji String.Split i String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0013 ZNACZĄCE |  
|Category|.NET Framework Usage Guidance|  
| Profilowanie metody | Próbkowanie |  
| Komunikat | Rozważ ograniczenie użycia funkcji String.Split i String.Substring. |  
| Typ reguły | Ostrzeżenie |  
  
## <a name="cause"></a>Przyczyna  
 Wywołania metod System.String.Split lub System.String.Substring jest znaczna część danych profilowania. Należy rozważyć użycie System.String.IndexOf lub System.String.IndexOfAny, jeśli testujesz istnienie podciągów w ciągu.  
  
## <a name="rule-description"></a>Opis reguły  
 Metoda Podziel operuje na obiekt ciągu i zwraca nową tablicę ciągów, która zawiera podciągów z oryginalnego. Funkcja przydziela pamięć dla obiektu zwróconej tablicy i przydziela nowy obiekt ciągu dla każdego elementu tablicy, które znajdzie. Podobnie metoda Substr operuje na obiekt ciągu i zwraca nowy ciąg, który jest odpowiednikiem podciągu, który otrzymał żądanie.  
  
 Jeśli zarządzanie alokacji pamięci ma kluczowe znaczenie dla aplikacji, należy rozważyć użycie alternatywy dla funkcji String.Split i String.Substr metod. Na przykład służy metoda IndexOf albo IndexOfAny aby zlokalizować podciąg określonego w ciągu znaków ciągu bez tworzenia nowego wystąpienia klasy String.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widok szczegółów funkcji](../profiling/function-details-view.md) pobierania próbek danych jej profilu. Sprawdź wywołania funkcji można znaleźć w sekcjach program najczęściej wykorzystać System.String.Split lub System.String.Substr metod. Jeśli jest to możliwe, należy użyć metody IndexOf albo IndexOfAny aby zlokalizować podciąg określonego w ciągu znaków ciągu bez tworzenia nowego wystąpienia klasy String.
