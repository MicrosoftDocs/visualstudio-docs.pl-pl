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
ms.openlocfilehash: 0312c0e40f3addd7952c136e95f3756091ba4dcb
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547392"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: Parametry identyfikatora URI nie powinny być ciągami

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ deklaruje metodę z parametrem ciągu, którego nazwa zawiera "URI", "URI", "urn", "urn", "URL" lub "URL", a typ nie deklaruje odpowiedniego przeciążenia, które pobiera <xref:System.Uri?displayProperty=fullName> parametr.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Ta reguła dzieli nazwę parametru na tokeny na podstawie Konwencji notacji CamelCase wielkości liter i sprawdza, czy każdy token jest równy "URI", "URI", "urn", "urn", "URL" lub "URL". Jeśli istnieje dopasowanie, reguła zakłada, że parametr reprezentuje jednolity identyfikator zasobów (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. Jeśli metoda przyjmuje ciąg reprezentujący identyfikator URI, należy dostarczyć odpowiednie Przeciążenie, które przyjmuje wystąpienie <xref:System.Uri> klasy, które udostępnia te usługi w bezpieczny i bezpieczny sposób.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zmienić parametr na <xref:System.Uri> typ; jest to istotna zmiana. Alternatywnie Podaj Przeciążenie metody, która przyjmuje <xref:System.Uri> parametr; jest to nieprzerwana zmiana.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli parametr nie reprezentuje identyfikatora URI, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1054.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, `ErrorProne`, który narusza tę regułę i `SaferWay`typ, który spełnia regułę.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1055: Zwracane wartości identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234 Przekaż obiekty System. URI zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Przeciążenia identyfikatora URI ciągu wywołania system. URI overloads](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)