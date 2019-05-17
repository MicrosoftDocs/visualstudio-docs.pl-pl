---
title: 'CA1721: Nazwy właściwości nie powinny być takie same jak nazwy metod Get'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bf16a9edf25132aa8b58702f01563b8d7ccf109a
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841492"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Nazwy właściwości nie powinny być takie same jak nazwy metod Get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa elementu członkowskiego zaczyna się od "Get" i odpowiada nazwie właściwości. Na przykład typ, który zawiera metodę o nazwie "Getcolor —" i właściwość, która nosi nazwę "Color" może spowodować naruszenie reguły.

Domyślnie ta reguła przegląda tylko właściwości i elementów członkowskich widocznych zewnętrznie, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Metody „Get” i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje.

Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Ten spójności skraca czas, są wymagane, aby dowiedzieć się nowa Biblioteka oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień nazwę, tak aby nazwę metody, która jest poprzedzony znakiem "Get" nie pasuje.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

> [!NOTE]
> Jeżeli metoda "Get" jest spowodowany przez zaimplementowanie interfejsu iextenderprovider — można wyłączyć to ostrzeżenie.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1721.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazewnictwa). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy przykład zawiera metody i właściwości, które spełniają tej reguły.

[!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
[!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1024: Korzystanie z właściwości, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)