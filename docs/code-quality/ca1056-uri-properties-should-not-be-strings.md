---
title: 'CA1056: Właściwości identyfikatora URI nie powinny być ciągami'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 71e365fa0891e9cb01f7a2860a9c2f13b78072b3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235529"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: Właściwości identyfikatora URI nie powinny być ciągami

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ deklaruje Właściwość ciągu, której nazwa zawiera "URI", "URI", "urn", "urn", "URL" lub "URL".

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Ta reguła dzieli nazwę właściwości na tokeny na podstawie Konwencji dotyczącej wielkości liter Pascala i sprawdza, czy każdy token jest równy "URI", "URI", "urn", "urn", "URL" lub "URL". W przypadku dopasowania reguła zakłada, że właściwość reprezentuje identyfikator URI (Uniform Resource Identifier). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri?displayProperty=fullName> Klasa udostępnia te usługi w bezpieczny i bezpieczny sposób.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zmień właściwość na <xref:System.Uri> typ.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli właściwość nie reprezentuje identyfikatora URI, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1056.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, `ErrorProne`, który narusza tę regułę i `SaferWay`typ, który spełnia regułę.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055: Zwracane wartości identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234 Przekaż obiekty System. URI zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Przeciążenia identyfikatora URI ciągu wywołania system. URI overloads](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)