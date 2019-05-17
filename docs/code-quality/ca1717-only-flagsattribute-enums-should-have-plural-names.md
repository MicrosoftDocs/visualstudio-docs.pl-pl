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
ms.openlocfilehash: e73359764da2b07371f0dfd0ff023a704dd7465c
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841855"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa wyliczenia kończy się w liczbie mnogiej programu word i wyliczenia nie jest oznaczony atrybutem <xref:System.FlagsAttribute?displayProperty=fullName> atrybutu.

Domyślnie ta reguła przegląda tylko wyliczenia widocznego na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Nazwa w liczbie mnogiej dla wyliczenia wskazuje, jednocześnie określono więcej niż jedną wartość wyliczenia zgodnie z konwencjami nazewnictwa. <xref:System.FlagsAttribute> Kompilatory informuje, że wyliczenia powinny być traktowane jako pola bitowe, które umożliwia wykonywanie operacji bitowa na wyliczeniu.

Jeśli tylko jedna z wartości wyliczenia można określić jednocześnie, nazwa wyliczenia powinna być pojedynczą programu word. Na przykład wyliczenie definiujące dni tygodnia, może być przeznaczona do użycia w aplikacji, której można określić wiele dni. To wyliczenie powinny mieć <xref:System.FlagsAttribute> i może być wywoływana "Dni". Podobne wyliczenie, które umożliwia określenie tylko jednego dnia nie miałoby atrybutu i może być o nazwie "Day".

Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to czas, który jest wymagany, aby dowiedzieć się nowa Biblioteka oprogramowania i zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Wprowadź nazwę wyliczenia pojedynczej programu word lub dodać <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie z reguły, jeśli nazwa kończy się na pojedynczej programu word.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1717.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazewnictwa). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1714: Typy wyliczeniowe flag powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1714-flags-enums-should-have-plural-names.md)
- [CA1027: Oznacz Typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Projekt wyliczeń](/dotnet/standard/design-guidelines/enum)