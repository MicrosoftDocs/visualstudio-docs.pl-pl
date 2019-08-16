---
title: 'CA1714: Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej'
ms.date: 03/11/2019
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
ms.openlocfilehash: d71200c6c7fbb61e7994119fde5e75f7623fa669
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547192"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Wyliczenie ma <xref:System.FlagsAttribute?displayProperty=fullName> i jego nazwę nie kończy się znakiem ".

Domyślnie ta reguła sprawdza się tylko na wyliczeniu widocznym na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Typy oznaczone nazwą mają nazwy <xref:System.FlagsAttribute> , które są w liczbie mnogiej, ponieważ atrybut wskazuje, że można określić więcej niż jedną wartość. Na przykład Wyliczenie definiujące dni tygodnia może być przeznaczone do użycia w aplikacji, w której można określić wiele dni. To Wyliczenie powinno mieć wartość <xref:System.FlagsAttribute> i może być nazywane "dniami". Podobne Wyliczenie, które zezwala na określenie tylko jednego dnia, nie ma atrybutu i może być wywołane "Day".

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień nazwę wyliczenia na słowo w liczbie mnogiej lub Usuń <xref:System.FlagsAttribute> atrybut, jeśli nie można jednocześnie określić wielu wartości wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli nazwa jest słowem w liczbie mnogiej, ale nie kończy się znakiem ", można bezpiecznie pominąć naruszenie. Na przykład, jeśli Wyliczenie wielodniowe, które zostało opisane wcześniej miało nazwę "DaysOfTheWeek", spowoduje to naruszenie logiki reguły, ale nie jej potrzeby. Takie naruszenia powinny być pomijane.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1714.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazywanie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1027 Oznacz typy wyliczeniowe atrybutem FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Projekt wyliczenia](/dotnet/standard/design-guidelines/enum)