---
title: 'CA1711: Identyfikatory nie powinny mieć nieprawidłowych sufiksów'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e04487a9bfcd8ef9a0e9a15bc76a93b221f9ce1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234144"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Identyfikatory nie powinny mieć nieprawidłowych sufiksów

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Kategoria|Microsoft.Naming|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Identyfikator ma niepoprawny sufiks.

Domyślnie ta reguła sprawdza tylko widoczne na zewnątrz identyfikatory, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Zgodnie z Konwencją, tylko nazwy typów, które poszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, powinny kończyć się określonymi zastrzeżonymi sufiksami. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów.

W poniższej tabeli wymieniono zastrzeżone sufiksy i typy podstawowe oraz interfejsy, z którymi są skojarzone.

|Suffix|Typ podstawowy/interfejs|
|------------|--------------------------|
|Atrybut|<xref:System.Attribute?displayProperty=fullName>|
|Kolekcja|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|Delegat programu obsługi zdarzeń|
|Wyjątek|<xref:System.Exception?displayProperty=fullName>|
|Uprawnienie|<xref:System.Security.IPermission?displayProperty=fullName>|
|Kolejka|<xref:System.Collections.Queue?displayProperty=fullName>|
|Stos|<xref:System.Collections.Stack?displayProperty=fullName>|
|Strumień|<xref:System.IO.Stream?displayProperty=fullName>|

Ponadto **nie** należy używać następujących sufiksów:

- `Delegate`

- `Enum`

- `Impl`(Użyj `Core` zamiast tego)

- `Ex`lub podobnego sufiksu, aby odróżnić go od wcześniejszej wersji tego samego typu

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Usuń sufiks z nazwy typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżenia z tej reguły, chyba że sufiks ma niejednoznaczne znaczenie w domenie aplikacji.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1711.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazywanie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>Zobacz także

- [Atrybuty](/dotnet/standard/design-guidelines/attributes)
- [Obsługa i wywoływanie zdarzeń](/dotnet/standard/events/index)