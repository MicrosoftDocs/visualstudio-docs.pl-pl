---
title: 'CA2006: Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0e671deab060346bb998932495e5590f19945eaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233103"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategoria|Microsoft.Reliability|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Kod zarządzany używa <xref:System.IntPtr> do uzyskiwania dostępu do zasobów natywnych.

## <a name="rule-description"></a>Opis reguły

`IntPtr` Użycie w kodzie zarządzanym może wskazywać na potencjalny problem z zabezpieczeniami i niezawodnością. Wszystkie zastosowania programu `IntPtr` muszą zostać zweryfikowane w celu ustalenia, czy w <xref:System.Runtime.InteropServices.SafeHandle> jego miejscu wymagane jest użycie lub Podobna technologia. Występują problemy, jeśli `IntPtr` reprezentuje jakiś zasób natywny, taki jak pamięć, dojście do pliku lub gniazdo, że kod zarządzany jest traktowany jako własny. Jeśli zarządzany kod jest właścicielem zasobu, musi również zwolnić natywne skojarzone z nim zasoby, ponieważ nie spowoduje to powstania wycieku zasobów.

W takich scenariuszach istnieją również problemy z zabezpieczeniami lub niezawodnością, jeśli dostęp wielowątkowy jest dozwolony do `IntPtr` i w sposób umożliwiający zwolnienie zasobu reprezentowanego `IntPtr` przez program. Te problemy obejmują odtwarzanie `IntPtr` wartości w wydaniu zasobów podczas jednoczesnego używania zasobu w innym wątku. Może to spowodować sytuacje wyścigu, w których jeden wątek może odczytywać lub zapisywać dane skojarzone z niewłaściwym zasobem. Na przykład, jeśli typ przechowuje dojście systemu operacyjnego jako `IntPtr` i umożliwia użytkownikom wywoływanie zarówno **zamknięcia** , jak i innej metody, która używa tego uchwytu jednocześnie i bez pewnego rodzaju synchronizacji, kod ma problem z odtwarzaniem obsługi.

Ten problem z odtwarzaniem obsłudze może spowodować uszkodzenie danych i często lukę w zabezpieczeniach. `SafeHandle`i jej klasy <xref:System.Runtime.InteropServices.CriticalHandle> równorzędnej zapewniają mechanizm hermetyzowania natywnego uchwytu do zasobu, co pozwala uniknąć takich problemów z wątkami. Ponadto można użyć `SafeHandle` klasy `CriticalHandle` i jej elementów równorzędnych do innych problemów związanych z wątkami, na przykład w celu starannej kontroli okresu istnienia zarządzanych obiektów, które zawierają kopię natywnego uchwytu w przypadku wywołań metod natywnych. W takiej sytuacji często można usunąć wywołania do `GC.KeepAlive`. Narzuty wydajności, które naliczane podczas `SafeHandle` korzystania z i, w mniejszym `CriticalHandle`stopniu, mogą być często ograniczone poprzez staranne projektowanie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Konwertuj `IntPtr` użycie na `SafeHandle` , aby bezpiecznie zarządzać dostępem do zasobów natywnych. Przykłady można znaleźć w artykule referencyjnym.<xref:System.Runtime.InteropServices.SafeHandle>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj tego ostrzeżenia.

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable>