---
title: 'CA1714: Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 512e66c65cb3abd0b5e56f268b9a89e4d51758bf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953910"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Publiczne wyliczenie ma <xref:System.FlagsAttribute?displayProperty=fullName> i jego nazwa nie kończy się w firmy ".

## <a name="rule-description"></a>Opis reguły
 Typy, które są oznaczone <xref:System.FlagsAttribute> mają nazwy, które mają liczbę mnogą, ponieważ ten atrybut wskazuje, że można określić więcej niż jedną wartość. Na przykład wyliczenie definiujące dni tygodnia, może być przeznaczona do użycia w aplikacji, której można określić wiele dni. To wyliczenie powinny mieć <xref:System.FlagsAttribute> i może być wywoływana "Dni". Podobne wyliczenie, które umożliwia określenie tylko jednego dnia nie miałoby atrybutu i może być o nazwie "Day".

 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wprowadź nazwę wyliczenia mnogą słowa lub usunąć <xref:System.FlagsAttribute> atrybutu, jeśli wiele wartości wyliczenia nie powinny być określone jednocześnie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne pominąć to naruszenie, jeśli nazwa jest słowem w liczbie mnogiej, ale nie kończy się na ". Na przykład jeśli wyliczenie wiele dni, który został opisany wcześniej o nazwach "DaysOfTheWeek", to naruszyć logiką reguły, ale nie jej przeznaczenie. Powinno być pomijane te naruszenia.

## <a name="related-rules"></a>Powiązane reguły
 [CA1027: Oznacz Typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Projekt wyliczeń](/dotnet/standard/design-guidelines/enum)