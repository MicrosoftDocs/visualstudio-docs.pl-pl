---
title: 'DA0010: Drogie GetHashCode | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9ce982c7a98fd12749c66c89e47bd895d2fb6a5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777689"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Expensive GetHashCode

|||
|-|-|
|Identyfikator reguły|DA0010|
|Kategoria|Użycie programu .NET Framework|
|Metody profilowania|Próbkowanie<br /><br /> Pamięć .NET|
|Komunikat|Funkcje GetHashCode powinny być tanie i nie przydzielać żadnej pamięci. Zmniejsz złożoność funkcji kodu mieszania, jeśli to możliwe.|
|Typ wiadomości|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania GetHashCode metody typu są znaczną część danych profilowania lub metoda przydziela pamięci.

## <a name="rule-description"></a>Opis reguły
 Mieszanie jest techniką szybkiego lokalizowania określonego elementu w dużej kolekcji. Ponieważ tabele mieszania mogą być duże i muszą obsługiwać bardzo wysokie stawki dostępu, tabele skrótów powinny być wydajne. Implikacją tego wymagania jest, że Metody GetHashCode w .NET Framework nie należy przydzielić pamięci. Przydzielanie pamięci zwiększa obciążenie modułu zbierającego elementy bezużyteczne i udostępnia metodę do potencjalnych opóźnień, jeśli staje się konieczne uruchomienie wyrzucania elementów bezużytecznych w wyniku żądania alokacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmniejsz złożoność metody.
