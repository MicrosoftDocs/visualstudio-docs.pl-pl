---
title: 'CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6c0a03f68ed15e790ea8a43a9ae2b476dd2f6f5d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235550"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa metody zawiera "URI", "URI", "urn", "urn", "URL" lub "URL", a metoda zwraca ciąg.

Domyślnie ta reguła sprawdza tylko metody publiczne, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Ta reguła dzieli nazwę metody na tokeny na podstawie Konwencji dotyczącej wielkości liter Pascala i sprawdza, czy każdy token jest równy "URI", "URI", "urn", "urn", "URL" lub "URL". W przypadku dopasowania reguła zakłada, że metoda zwraca jednolity identyfikator zasobów (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri?displayProperty=fullName> Klasa udostępnia te usługi w bezpieczny i bezpieczny sposób.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zmień zwracany typ na <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wartość zwracana nie reprezentuje identyfikatora URI, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1055.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, `ErrorProne`, który narusza tę regułę i `SaferWay`typ, który spełnia regułę.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234 Przekaż obiekty System. URI zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Przeciążenia identyfikatora URI ciągu wywołania system. URI overloads](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)