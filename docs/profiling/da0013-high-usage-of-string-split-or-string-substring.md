---
title: 'DA0013: wysokie użycie metody String. Split lub String. substring | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d42469ac5236a41eda96af5d1fe896a5ed84a321
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779411"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Znaczące wykorzystanie String.Split lub String.Substring

|||
|-|-|
|Identyfikator zasady|DA0013|
|Kategoria|Wskazówki dotyczące .NET Framework|
|Metody profilowania|Sond|
|Komunikat|Rozważ ograniczenie użycia funkcji String. Split i String. substring.|
|Typ reguły|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania metody System. String. Split lub system. String. substring są istotną częścią danych profilowania. Rozważ użycie elementu System. String. IndexOf lub system. String. IndexOfAny, jeśli testujesz istnienie podciągu w ciągu.

## <a name="rule-description"></a>Opis reguły
 Metoda Split działa na obiekcie String i zwraca nową tablicę ciągów, która zawiera podciągi oryginału. Funkcja przydziela pamięć dla zwracanego obiektu array i przydziela nowy obiekt ciągu dla każdego elementu tablicy, który znajdzie. Podobnie Metoda substr działa na obiekcie String i zwraca nowy ciąg, który jest odpowiednikiem żądanego podciągu.

 Jeśli Zarządzanie alokacją pamięci ma krytyczne znaczenie dla aplikacji, należy rozważyć użycie alternatywnych metod String. Split i String. substr. Na przykład można użyć metody IndexOf lub IndexOfAny, aby zlokalizować konkretny podciąg w ciągu znaków bez tworzenia nowego wystąpienia klasy String.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie **Lista błędów** , aby przejść do [widoku Szczegóły funkcji](../profiling/function-details-view.md) danych profilu próbkowania. Sprawdź funkcje wywołujące, aby znaleźć sekcje programu, które są najczęściej używane metody System. String. Split lub system. String. substr. Jeśli to możliwe, użyj metody IndexOf lub IndexOfAny, aby zlokalizować konkretny podciąg w ciągu znaków bez tworzenia nowego wystąpienia klasy String.
