---
title: 'CA1054: Parametry identyfikatora URI nie powinny być ciągami'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 659ea1008cd70571d035d0b178d01587c6b2ba0d
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842067"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: Parametry identyfikatora URI nie powinny być ciągami

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ deklaruje metodę z parametrem ciągu, którego nazwa zawiera "uri", "Uri", "urn", "Urn", "url" lub "Url" i typ nie deklaruje odpowiadające przeciążenie, która przyjmuje <xref:System.Uri?displayProperty=fullName> parametru.

Domyślnie ta reguła przegląda tylko typy widoczne na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Ta reguła dzieli nazwę parametru na tokeny oparte na Konwencji camelcase i sprawdza, czy każdy token jest równa "uri", "Uri", "urn", "Urn", "url" lub "Url". Jeśli istnieje dopasowanie, reguła zakłada, że parametr reprezentuje identyfikator uniform resource identifier (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Jeśli metoda pobiera reprezentację ciągu identyfikatora URI, odpowiadające przeciążenie powinien być podany, pobierające wystąpienie z <xref:System.Uri> klasy, która udostępnia te usługi w bezpieczny sposób.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Zmień parametr <xref:System.Uri> wpisz; to jest zmianą przerywającą. Alternatywnie, zapewnienia przeciążenia metody, która przyjmuje <xref:System.Uri> parameter; to zmian niepowodujących niezgodności.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr nie reprezentuje identyfikator URI.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1054.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano typem `ErrorProne`, który narusza tę regułę, a typem `SaferWay`, odpowiadającej reguły.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1055: Identyfikator URI zwracanych wartości nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234: Przekazuj obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Przeciążenia identyfikatora URI ciągu wywołują przeciążenia System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)