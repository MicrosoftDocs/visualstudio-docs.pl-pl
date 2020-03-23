---
title: 'DA0013: Wysokie użycie string.split lub string.substring | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779411"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Znaczące wykorzystanie String.Split lub String.Substring

|||
|-|-|
|Identyfikator reguły|DA0013|
|Kategoria|Wskazówki dotyczące użycia programu .NET Framework|
|Metody profilowania|Próbkowanie|
|Komunikat|Należy rozważyć zmniejszenie użycia string.split i String.Substring funkcji.|
|Typ reguły|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania metody System.String.Split lub System.String.Substring stanowią znaczną część danych profilowania. Należy rozważyć użycie System.String.IndexOf lub System.String.IndexOfAny, jeśli testujesz podciąg w ciągu.

## <a name="rule-description"></a>Opis reguły
 Split Metoda działa na String obiektu i zwraca nową tablicę Strings, który posiada podciągi oryginału. Funkcja przydziela pamięć dla zwróconego obiektu tablicowego i przydziela nowy obiekt String dla każdego elementu tablicy, który znajdzie. Podobnie substr metoda działa na String obiektu i zwraca nowy String, który jest odpowiednikiem żądanego podciągu.

 Jeśli zarządzanie alokacji pamięci ma kluczowe znaczenie w aplikacji, należy rozważyć użycie alternatyw dla String.Split i String.Substr metody. Na przykład można użyć IndexOf lub IndexOfAny metody, aby zlokalizować określonego podciąg w ciągu znaku bez tworzenia nowego wystąpienia String klasy.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie **Lista błędów,** aby przejść do [widoku szczegóły funkcji](../profiling/function-details-view.md) danych profilu próbkowania. Sprawdź funkcje wywołujące, aby znaleźć sekcje programu, które najczęściej korzystają z metod System.String.Split lub System.String.Substr. Jeśli to możliwe, użyj IndexOf lub IndexOfAny metody, aby zlokalizować określonego podciąg w ciągu znaków bez tworzenia nowego wystąpienia String klasy.
