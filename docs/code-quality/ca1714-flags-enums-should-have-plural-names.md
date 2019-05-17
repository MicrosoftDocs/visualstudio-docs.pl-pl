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
ms.openlocfilehash: 24a412161d9f91830486378d4e8228386cfd3fb7
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841901"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Wyliczenie ma <xref:System.FlagsAttribute?displayProperty=fullName> i jego nazwa nie kończy się w firmy ".

Domyślnie ta reguła przegląda tylko wyliczenia widocznego na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Typy, które są oznaczone <xref:System.FlagsAttribute> mają nazwy, które mają liczbę mnogą, ponieważ ten atrybut wskazuje, że można określić więcej niż jedną wartość. Na przykład wyliczenie definiujące dni tygodnia, może być przeznaczona do użycia w aplikacji, której można określić wiele dni. To wyliczenie powinny mieć <xref:System.FlagsAttribute> i może być wywoływana "Dni". Podobne wyliczenie, które umożliwia określenie tylko jednego dnia nie miałoby atrybutu i może być o nazwie "Day".

Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Wprowadź nazwę wyliczenia mnogą słowa lub usunąć <xref:System.FlagsAttribute> atrybutu, jeśli wiele wartości wyliczenia nie powinny być określone jednocześnie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest to bezpieczne pominąć to naruszenie, jeśli nazwa jest słowem w liczbie mnogiej, ale nie kończy się na ". Na przykład jeśli wyliczenie wiele dni, który został opisany wcześniej o nazwach "DaysOfTheWeek", to naruszyć logiką reguły, ale nie jej przeznaczenie. Powinno być pomijane te naruszenia.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1714.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazewnictwa). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1027: Oznacz Typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Nie oznaczaj wyliczeń za pomocą FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Projekt wyliczeń](/dotnet/standard/design-guidelines/enum)