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
ms.openlocfilehash: 6d29eb9475d48e634766df65836162d6a79fed77
ms.sourcegitcommit: 1024f336dcd8e8a4c50b9a9ad8ec85b6e70073a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57699632"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Zarządzany kod używa <xref:System.IntPtr> dostęp do zasobów natywnych.

## <a name="rule-description"></a>Opis reguły

Korzystanie z `IntPtr` w kodzie zarządzanym może wskazywać na potencjalny problem zabezpieczeń i niezawodności. Wszystkie przypadki użycia `IntPtr` muszą być przejrzane w celu określenia czy użytkowania <xref:System.Runtime.InteropServices.SafeHandle> , lub podobnej technologii jest wymagany w tym miejscu. Problemy z wystąpi `IntPtr` reprezentuje niektóre zasobu natywnego, takich jak pamięć, dojścia do pliku lub gniazdo, że kod zarządzany jest uważany za własne. Jeśli kod zarządzany jest właścicielem zasobu, jego również zwolnić macierzystymi zasobami, które są skojarzone z nią, ponieważ niewykonanie tej czynności mogłoby spowodować wycieki zasobów.

W takich przypadkach problemy z zabezpieczeniami lub niezawodność będą dostępne są także jeśli dostęp do wielu wątków może być `IntPtr` i sposób przy zwalnianiu zasobów, który jest reprezentowany przez `IntPtr` podano. Te problemy obejmują recyklingu `IntPtr` wartość w wersji zasobu w trakcie jednoczesne użycie zasobów w innym wątku. Może to spowodować sytuacje wyścigu, gdzie jeden wątek może odczytu lub zapisu danych, który jest skojarzony z niewłaściwego zasobu. Na przykład, jeśli danego typu przechowuje dojście systemu operacyjnego jako `IntPtr` . Umożliwia ono użytkownikom wywołać oba **Zamknij** i innych metod, które używa dojścia równocześnie, jak i bez pewnego rodzaju synchronizacji, kod ma uchwyt odtwarzania Wystąpił problem.

Tego dojścia do odtwarzania problem może spowodować uszkodzenie danych, a często luki w zabezpieczeniach. `SafeHandle` i jego klasa element równorzędny <xref:System.Runtime.InteropServices.CriticalHandle> mechanizm do hermetyzacji natywnych dojście do zasobu, dzięki czemu można uniknąć tych problemów wątków. Ponadto można użyć `SafeHandle` i jego klasa element równorzędny `CriticalHandle` dla innych wątków problemów, na przykład dokładnie kontrolować okres istnienia zarządzanych obiektów, które zawierają kopię uchwyt macierzysty za pośrednictwem wywołania metod natywnych. W takiej sytuacji można często wyeliminować wywołania `GC.KeepAlive`. Zmniejszenie wydajności, która wiąże się, gdy używasz `SafeHandle` i w mniejszym stopniu `CriticalHandle`, często można zmniejszyć za pomocą zachowania ostrożności podczas projektowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Konwertuj `IntPtr` wykorzystania `SafeHandle` bezpieczne zarządzanie dostępem do zasobów natywnych. Zobacz <xref:System.Runtime.InteropServices.SafeHandle> artykuł dokumentacji, przykładów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie Pomijaj to ostrzeżenie.

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable>