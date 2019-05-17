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
ms.openlocfilehash: 4517fc0d0dbfedc59a5a621f894d7e1d77b35c38
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842175"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa metody zawiera "uri", "Uri", "urn", "Urn", "url" lub "Url", a metoda zwraca wartość typu ciąg.

Domyślnie ta reguła przegląda tylko metody publiczne, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Ta reguła dzieli nazwę metody na tokeny oparte na Konwencji obudowy Pascal i sprawdza, czy każdy token jest równa "uri", "Uri", "urn", "Urn", "url" lub "Url". Jeśli istnieje dopasowanie, reguła zakłada, że metoda zwraca identyfikator uniform resource identifier (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri?displayProperty=fullName> Klasa udostępnia te usługi w bezpieczny sposób.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zmienić typ zwracany <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli wartość zwracana nie reprezentuje identyfikator URI.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1055.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano typem `ErrorProne`, który narusza tę regułę, a typem `SaferWay`, odpowiadającej reguły.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234: Przekazuj obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Przeciążenia identyfikatora URI ciągu wywołują przeciążenia System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)