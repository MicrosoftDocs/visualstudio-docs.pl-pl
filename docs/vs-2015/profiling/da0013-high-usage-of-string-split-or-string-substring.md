---
title: 'DA0013: wysokie użycie metody String. Split lub String. substring | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159193"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Znaczące wykorzystanie funkcji String.Split i String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0013 |  
| Kategoria |. Wskazówki dotyczące użycia platformy NET Framework |  
| Metody profilowania | Próbkowanie |  
| Komunikat | Rozważ ograniczenie użycia funkcji String. Split i String. substring. |  
| Typ reguły | Ostrzeżenie |  
  
## <a name="cause"></a>Przyczyna  
 Wywołania metody System. String. Split lub system. String. substring są istotną częścią danych profilowania. Rozważ użycie elementu System. String. IndexOf lub system. String. IndexOfAny, jeśli testujesz istnienie podciągu w ciągu.  
  
## <a name="rule-description"></a>Opis reguły  
 Metoda Split działa na obiekcie String i zwraca nową tablicę ciągów, która zawiera podciągi oryginału. Funkcja przydziela pamięć dla zwracanego obiektu array i przydziela nowy obiekt ciągu dla każdego elementu tablicy, który znajdzie. Podobnie Metoda substr działa na obiekcie String i zwraca nowy ciąg, który jest odpowiednikiem żądanego podciągu.  
  
 Jeśli Zarządzanie alokacją pamięci ma krytyczne znaczenie dla aplikacji, należy rozważyć użycie alternatywnych metod String. Split i String. substr. Na przykład można użyć metody IndexOf lub IndexOfAny, aby zlokalizować konkretny podciąg w ciągu znaków bez tworzenia nowego wystąpienia klasy String.  
  
## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku Szczegóły funkcji](../profiling/function-details-view.md) danych profilu próbkowania. Sprawdź funkcje wywołujące, aby znaleźć sekcje programu, które są najczęściej używane metody System. String. Split lub system. String. substr. Jeśli jest to możliwe, użyj metody IndexOf lub IndexOfAny, aby zlokalizować konkretny podciąg w ciągu znaków bez tworzenia nowego wystąpienia klasy String.
