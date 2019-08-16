---
title: 'CA1717: Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d760802422773b3713fa7ea08ce0ce7a191f418
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547117"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa wyliczenia zostaje zakończona w słowie w liczbie mnogiej, a Wyliczenie nie jest oznaczone <xref:System.FlagsAttribute?displayProperty=fullName> atrybutem.

Domyślnie ta reguła sprawdza się tylko na wyliczeniu widocznym na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Konwencje nazewnictwa wymuszają, że nazwa w liczbie mnogiej dla wyliczenia wskazuje, że można określić więcej niż jedną wartość wyliczenia jednocześnie. <xref:System.FlagsAttribute> Informuje kompilatory, że Wyliczenie powinno być traktowane jako pole bitowe, które włącza operacje bitowe na wyliczeniu.

Jeśli można określić tylko jedną wartość wyliczenia, nazwa wyliczenia powinna być słowem jednopojedynczym. Na przykład Wyliczenie definiujące dni tygodnia może być przeznaczone do użycia w aplikacji, w której można określić wiele dni. To Wyliczenie powinno mieć wartość <xref:System.FlagsAttribute> i może być nazywane "dniami". Podobne Wyliczenie, które zezwala na określenie tylko jednego dnia, nie ma atrybutu i może być wywołane "Day".

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Pozwala to skrócić czas wymagany do nauczenia się nowej biblioteki oprogramowania i zwiększyć zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Wprowadź nazwę wyliczenia jako pojedyncze słowo lub Dodaj <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli nazwa zostanie zakończona pojedynczym słowem, można bezpiecznie pominąć ostrzeżenie z reguły.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1717.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazywanie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1714 Wyliczenia flag powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1714-flags-enums-should-have-plural-names.md)
- [CA1027 Oznacz typy wyliczeniowe atrybutem FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Projekt wyliczenia](/dotnet/standard/design-guidelines/enum)