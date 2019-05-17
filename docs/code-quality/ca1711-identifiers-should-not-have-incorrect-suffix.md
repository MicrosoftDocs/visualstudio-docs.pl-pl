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
ms.openlocfilehash: 9377dcf03bcbb8087d152ef98986f31c12c94c45
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841928"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Identyfikatory nie powinny mieć nieprawidłowych sufiksów

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Identyfikator ma niepoprawnego sufiksu.

Domyślnie ta reguła przegląda tylko identyfikatory widocznego na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Według Konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, powinien kończyć się określonym zarezerwowanym sufiksem. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów.

W poniższej tabeli wymieniono zarezerwowanym sufiksem i typy podstawowe i interfejsy, z którymi są skojarzone.

|Suffix|Interfejs podstawowy|
|------------|--------------------------|
|Atrybut|<xref:System.Attribute?displayProperty=fullName>|
|Kolekcja|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Słownik|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|Delegat programu obsługi zdarzeń|
|Wyjątek|<xref:System.Exception?displayProperty=fullName>|
|Uprawnienie|<xref:System.Security.IPermission?displayProperty=fullName>|
|Kolejka|<xref:System.Collections.Queue?displayProperty=fullName>|
|Stos|<xref:System.Collections.Stack?displayProperty=fullName>|
|Strumień|<xref:System.IO.Stream?displayProperty=fullName>|

Ponadto następujące sufiksy powinny **nie** można użyć:

- `Delegate`

- `Enum`

- `Impl` (Użyj `Core` zamiast)

- `Ex` lub podobny sufiksu w odróżnieniu od starszej wersji tego samego typu

Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Usuń sufiks z nazwą typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły, chyba że sufiksem ma jednoznaczną znaczenie w domenie aplikacji.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1711.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazewnictwa). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

- [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>Zobacz także

- [Atrybuty](/dotnet/standard/design-guidelines/attributes)
- [Obsługa i wywoływanie zdarzeń](/dotnet/standard/events/index)