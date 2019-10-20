---
title: 'CA2107: przegląd użycia tylko Odmów i Zezwalaj na użycie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 32339852d67d4f3f28fedd204a056440ad49e075
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665967"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Przejrzyj użycie akcji Deny i Permit Only
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda zawiera sprawdzanie zabezpieczeń określające akcję zabezpieczeń PermitOnly lub Odmów.

## <a name="rule-description"></a>Opis reguły
 [Przy użyciu metody PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) i akcji zabezpieczeń <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> powinny być używane tylko przez te osoby, które mają zaawansowaną wiedzę o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zabezpieczeniach. Kod, który używa tych akcji zabezpieczeń, należy poddać przeglądowi zabezpieczeń.

 Odmowa powoduje zmianę domyślnego zachowania stosu, które występuje w odpowiedzi na żądanie zabezpieczeń. Pozwala określić uprawnienia, które nie mogą być przyznawane na czas trwania metody odmowy, niezależnie od faktycznych uprawnień wywołujących w stosie wywołań. Jeśli polecenie przeszukiwania stosu wykryje metodę, która jest zabezpieczona przez odmowę, a jeśli żądanie zostanie uwzględnione w uprawnieniach odmowy, przeszukiwanie stosu zakończy się niepowodzeniem. PermitOnly również zmienia domyślne zachowanie przeszukiwania stosu. Umożliwia kod, aby określić tylko te uprawnienia, które można przyznać, niezależnie od uprawnień do wywoływania. Jeśli polecenie przeszukiwania stosu wykryje metodę, która jest zabezpieczona przez PermitOnly, a jeśli żądanie nie zostanie uwzględnione w uprawnieniach, które są określone przez PermitOnly, przeszukiwanie stosu zakończy się niepowodzeniem.

 Kod, który opiera się na tych akcjach, należy dokładnie ocenić pod kątem luk w zabezpieczeniach ze względu na ograniczoną użyteczność i delikatne zachowanie. Rozważ następujące opcje:

- Nie ma to wpływ na [żądania dotyczące linków](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) lub PermitOnly.

- Jeśli Deny lub PermitOnly występuje w tej samej klatce stosu co żądanie, które powoduje przeprowadzenie stosu, akcje zabezpieczeń nie będą miały wpływu.

- Wartości, które są używane do konstruowania uprawnień opartych na ścieżkach, zazwyczaj można określić na wiele sposobów. Odmowa dostępu do jednej postaci ścieżki nie zezwala na dostęp do wszystkich formularzy. Na przykład, jeśli udział plików \\ \Server\Share jest mapowany na dysk sieciowy X:, aby odmówić dostępu do pliku w udziale, należy odmówić \\ \Server\Share\File, X:\File i każdej innej ścieżki, która uzyskuje dostęp do pliku.

- @No__t_0 może przerwać przechodzenie stosu przed osiągnięciem odmowy lub PermitOnly.

- Jeśli odmowa ma wpływ, a mianowicie, gdy obiekt wywołujący ma uprawnienie, które jest blokowane przez odmowę, obiekt wywołujący może uzyskać dostęp bezpośrednio do chronionego zasobu, pomijając odmowę. Podobnie, jeśli obiekt wywołujący nie ma uprawnienia Odmowa, przeszukiwanie stosu zakończy się niepowodzeniem bez odmowy.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wszelkie zastosowania tych akcji zabezpieczeń spowodują naruszenie. Aby naprawić naruszenie, nie należy używać tych akcji zabezpieczeń.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły tylko po zakończeniu przeglądu zabezpieczeń.

## <a name="example"></a>Przykład
 Poniższy przykład demonstruje pewne ograniczenia dotyczące Odmów.

 Następująca biblioteka zawiera klasę, która ma dwie metody, które są identyczne z wyjątkiem wymagań dotyczących zabezpieczeń, które chronią je.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Przykład
 W poniższej aplikacji przedstawiono skutki odmowy dla bezpiecznych metod z biblioteki.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Zapotrzebowanie: Odmów obiektu wywołującego nie ma wpływu na żądanie z potwierdzonym uprawnieniem.** 
**LinkDemand: Odmów obiektu wywołującego nie ma wpływu na LinkDemand z uprawnieniem potwierdzonym.** 
**LinkDemand: Odmów obiektu wywołującego nie ma wpływu na kod chroniony przez LinkDemand.** 
**LinkDemand: ten odmowa nie ma wpływu na Kod chroniony LinkDemand.**
## <a name="see-also"></a>Zobacz też
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName><xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Zasady bezpiecznego kodowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [przesłaniające kontrole zabezpieczeń](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [za pomocą metody PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
