---
title: 'CA1700: Nie nadawaj wartościom wyliczenia nazwy &#39;zastrzeżone&#39;'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7046daecf2a133d44836c178cb42b45a286bb4b6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018179"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Nie nadawaj wartościom wyliczenia nazwy &#39;zastrzeżone&#39;

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa elementu członkowskiego wyliczenia zawierają wyraz "reserved".

## <a name="rule-description"></a>Opis reguły

Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą. Nie powinni oczekiwać od użytkowników, aby zignorować członka, po prostu, ponieważ jego nazwa zawiera "reserved", ani nie może polegać na użytkownikom odczytywanie lub stosować się do dokumentacji. Ponadto ponieważ zarezerwowanych elementów członkowskich są wyświetlane w przeglądarkach obiektu i inteligentne zintegrowanych środowisk projektowych, może spowodować, że pomyłek o tym, które elementy członkowskie są rzeczywiście używane.

Zamiast korzystać z zastrzeżoną składową, Dodaj nowy element członkowski do wyliczenia w przyszłej wersji. W większości przypadków dodanie nowego elementu członkowskiego nie jest istotnej zmiany, tak długo, jak dodanie nie powoduje, że wartości oryginalnego składowych, aby zmienić.

Ograniczona liczba przypadków dodawania członka jest zmianą przerywającą nawet wtedy, gdy oryginalny członkowie zachować oryginalne wartości. Przede wszystkim nowy element członkowski nie może być zwracany z istniejących ścieżek kodu bez przerywania obiektów wywołujących, które używają `switch` (`Select` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instrukcji na wartość zwracaną obejmujący listę całego elementów członkowskich i który zgłosić wyjątek w przypadek domyślny. Pomocniczy kwestią jest, że kod klienta może nie obsługiwać zmiana w porównaniu z metody odbicia takich jak <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. W związku z tym czy nowy element członkowski został zwrócony z istniejących metod niezgodności aplikacji występuje z powodu użycie odbicia niska, jedynym rozwiązaniem nierozdzielający jest:

1. Dodaj nowe wyliczenie, które zawiera elementy członkowskie oryginalnego i nowe.

2. Oznacz oryginalnego wyliczenie atrybutem <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybutu.

   Wykonaj tę samą procedurę dla dowolnego typy widoczne na zewnątrz lub elementów członkowskich, które udostępnianie oryginalne wyliczenia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, usuń lub zmień nazwę elementu członkowskiego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest to bezpieczne Pomijaj ostrzeżeń dla tej reguły dla elementu członkowskiego, który jest obecnie używany, lub dla bibliotek, które wcześniej zostały wprowadzone do użytku.

## <a name="related-rules"></a>Powiązane reguły

[CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

[CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

[CA1028: Magazyn typu wyliczeniowego powinien być typu Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

[CA1008: Typy wyliczeniowe powinny mieć wartości zerowej](../code-quality/ca1008-enums-should-have-zero-value.md)

[CA1027: Oznacz Typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)