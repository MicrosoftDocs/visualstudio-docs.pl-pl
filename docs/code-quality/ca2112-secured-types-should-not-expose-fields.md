---
title: 'CA2112: Zabezpieczone typy nie powinny ujawniać pól'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d46c9fe1b97b5bdfb081150a44aa69363eced53
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922800"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Zabezpieczone typy nie powinny ujawniać pól

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera pola publiczne i jest zabezpieczony przez [zapotrzebowania na łącza](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Opis reguły
 Jeśli kod ma dostęp do wystąpienia typu zabezpieczonego przez żądanie łącza, kod nie musi spełniać zapotrzebowania na łącza, aby uzyskać dostęp do pól typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, ustawianie niepublicznych pól i dodać publiczny właściwości lub metody, które zwracają pola danych. Kontrole zabezpieczeń żądanie LinkDemand dla typów ochrony dostępu do właściwości i metod typu. Zabezpieczenia dostępu kodu nie ma zastosowania do pól.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Zarówno związane z zabezpieczeniami i dobrego projektowania należy naprawić naruszenia, wprowadzając nonpublic pola publiczne. Ostrzeżenie od tej reguły można pominąć, jeśli pole nie zawiera informacje, które powinny być zabezpieczone. Ponadto nie należy polegać na zawartości pola.

## <a name="example"></a>Przykład
 Poniższy przykład składa się z typu biblioteki (`SecuredTypeWithFields`) z polami niezabezpieczone, typu (`Distributor`), można utworzyć wystąpienia typu biblioteki i przekazuje omyłkowe wystąpień typów nie masz uprawnień do ich utworzenia i kodu aplikacji może odczytywać pól wystąpień, nawet jeśli nie ma uprawnienia, które zabezpiecza typu.

 Poniższy kod biblioteki narusza regułę.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example-1"></a>Przykład 1
 Aplikacja nie można utworzyć wystąpienia ze względu na żądanie łącza, które chroni zabezpieczonego typu. Następujące klasy umożliwia aplikacji, aby uzyskać wystąpienia typu zabezpieczonego.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example-2"></a>Przykład 2
 Następująca aplikacja ilustruje, jak to zrobić, bez uprawnienia dostępu metody zabezpieczonego typu, kod może uzyskać dostęp jej pola.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

Ten przykład generuje następujące wyniki:

```txt
Creating an instance of SecuredTypeWithFields.
Secured type fields: 22, 33
Changing secured type's field...
Cached Object fields: 99, 33
```

## <a name="related-rules"></a>Powiązane reguły

- [CA1051: Nie deklaruj widocznych pól wystąpienia](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Zobacz także

- [Zapotrzebowanie na łącza](/dotnet/framework/misc/link-demands)
- [Dane i modelowanie](/dotnet/framework/data/index)