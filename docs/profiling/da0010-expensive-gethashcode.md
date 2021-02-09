---
title: DA0010-drogie GetHashCode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fc9c1b35a78a8d9453ab35f201a120bc75134768
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916837"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Kosztowna funkcja GetHashCode

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0010|
|Kategoria|Użycie .NET Framework|
|Metody profilowania|Próbkowanie<br /><br /> Pamięć platformy .NET|
|Komunikat|Funkcje GetHashCode powinny być tanie i nie mogą przydzielać żadnej pamięci. Zmniejsz złożoność funkcji kodu skrótu, jeśli jest to możliwe.|
|Typ wiadomości|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania metody GetHashCode typu są znaczną częścią danych profilowania lub metoda przydziela pamięć.

## <a name="rule-description"></a>Opis reguły
 Mieszanie jest techniką szybkiego lokalizowania określonego elementu w dużej kolekcji. Ponieważ tabele skrótów mogą być duże i muszą obsługiwać bardzo wysokie stawki dostępu, tabele skrótów powinny być wydajne. Implikacje tego wymagania polega na tym, że metody GetHashCode w .NET Framework nie powinny przydzielić pamięci. Alokacja pamięci zwiększa obciążenie w module wyrzucania elementów bezużytecznych i uwidacznia metodę do potencjalnych opóźnień, jeśli konieczne jest uruchomienie wyrzucania elementów bezużytecznych w wyniku żądania alokacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmniejsz złożoność metody.
