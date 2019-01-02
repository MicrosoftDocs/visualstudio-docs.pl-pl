---
title: 'CA2107: Przegląd Odmów i permit only'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c8f4e108d8443816bf43dec9deb629a3a231822
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826104"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Przegląd Odmów i permit only

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda zawiera sprawdzanie zabezpieczeń, które określa akcji zabezpieczeń PermitOnly lub Odmów.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> Akcji zabezpieczeń powinny być używane tylko przez tych, którzy mają zaawansowaną wiedzę o zabezpieczeniach .NET Framework. Kod, który używa tych akcji zabezpieczeń, należy poddać przeglądowi zabezpieczeń.

 Odmów zmienia domyślne zachowanie przeszukiwania stosu, który występuje w odpowiedzi na żądania zabezpieczeń. Dzięki temu można określić uprawnienia, które nie muszą być przyznawane na czas trwania odmowy metody, niezależnie od rzeczywistego uprawnień obiektów wywołujących w stosie wywołań. Jeśli przejście przez stos wykrywa metody, która jest zabezpieczony przez Odmów, a Jeśli żądane uprawnienie jest zawarte w odmówionych uprawnień, przejście przez stos nie powiedzie się. PermitOnly również zmienia domyślne zachowanie przeszukiwania stosu. Umożliwia ona kod, aby określić te uprawnienia, które mogą być udzielane, niezależnie od uprawnień obiektom wywołującym. Jeśli przejście przez stos wykrywa metody, która jest zabezpieczony przez PermitOnly i żądane uprawnienie nie jest uwzględniony w uprawnieniach, które są określone przez PermitOnly, przejście przez stos nie powiedzie się.

 Kod, który opiera się na te akcje należy dokładnie ocenić dla luki w zabezpieczeniach ze względu na ograniczone użyteczność i zachowanie subtelne. Rozważ następujące opcje:

- [Link zapotrzebowanie](/dotnet/framework/misc/link-demands) nie dotyczy Deny lub PermitOnly.

- Jeśli Deny lub PermitOnly występuje w tej samej ramki stosu jako żądanie, która powoduje przejście przez stos, akcje zabezpieczeń nie mają wpływu.

- Zazwyczaj można określić wartości, które są używane do konstruowania uprawnień opartych na ścieżkę na wiele sposobów. Odmowa dostępu do tego samego formularza ścieżki nie odmowa dostępu do wszystkich formularzy. Na przykład jeśli udział pliku \\\Server\Share jest zamapowany dysk sieciowy X:, aby odmówić dostępu do plików w udziale, należy odmówić \\\Server\Share\File X:\File oraz każdej innej ścieżki, który uzyskuje dostęp do pliku.

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Przed osiągnięciem Deny lub PermitOnly może zakończyć przeszukiwania stosu.

- Jeśli stan odmowa ma żadnego efektu, to znaczy, gdy obiekt wywołujący ma uprawnienie, który jest zablokowany przez Odmów, obiekt wywołujący można dostępu do chronionego zasobu bezpośrednio, pomijanie Odmów. Podobnie jeśli obiekt wywołujący nie ma odmowy uprawnień, przejście przez stos może zakończyć się niepowodzeniem bez Odmów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Naruszenie zasad spowoduje, że każde użycie tych akcji zabezpieczeń. Aby naprawić naruszenie, nie należy używać tych akcji zabezpieczeń.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, tylko w przypadku, po zakończeniu przeglądu zabezpieczeń.

## <a name="example-1"></a>Przykład 1
 W poniższym przykładzie pokazano kilka ograniczeń Odmów.

 Następująca biblioteka zawiera klasę, która ma dwie metody, które są identyczne, z wyjątkiem wymogów bezpieczeństwa, które je chronić.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>Przykład 2
 Następującej aplikacji przedstawia skutki Odmów zabezpieczonej metod z biblioteki.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
Demand: Caller's Deny has no effect on Demand with the asserted permission.
LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.
LinkDemand: Caller's Deny has no effect with LinkDemand-protected code.
LinkDemand: This Deny has no effect with LinkDemand-protected code.
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
- <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)