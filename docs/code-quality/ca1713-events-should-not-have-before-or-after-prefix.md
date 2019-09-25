---
title: 'CA1713: Zdarzenia nie powinny mieć prefiksu „before” ani „after”'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 834c0f73a1fdc26f06c62e1c6e3a2d19372a244d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234104"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Zdarzenia nie powinny mieć prefiksu „before” ani „after”

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Kategoria|Microsoft.Naming|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Nazwa zdarzenia rozpoczyna się od "Before" lub "After".

## <a name="rule-description"></a>Opis reguły
Nazwy zdarzeń powinny opisywać akcję, która wywołuje zdarzenie. Nazwa powiązanych zdarzeń, które są wywoływane w określonej kolejności, używa czasu teraźniejszego lub przeszłego, aby wskazać względne położenie akcji w sekwencji. Na przykład podczas nadawania nazwy pary zdarzeń, które są wywoływane podczas zamykania zasobu, można nadać nazwę "zamykając" i "zamknięte" zamiast "BeforeClose" i "AfterClose".

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Usuń prefiks z nazwy zdarzenia i Rozważ zmianę nazwy w taki sposób, aby korzystała z obecności lub ostatnich dziesiątek zlecenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.