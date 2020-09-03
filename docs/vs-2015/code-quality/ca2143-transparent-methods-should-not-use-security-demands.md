---
title: 'CA2143: Metody przezroczyste nie powinny używać żądań zabezpieczeń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca8f049da83b99da7d36ebf74e756dd95f738d64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546474"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Metody przezroczyste nie powinny używać żądań zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ tranparent lub metoda jest deklaratywnie oznaczona z <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` zapotrzebowaniem lub metoda wywołuje <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> metodę.

## <a name="rule-description"></a>Opis reguły
 Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Przejrzysty pod względem bezpieczeństwa kod powinien używać pełnych żądań do podejmowania decyzji związanych z zabezpieczeniami, a kod krytyczny pod względem zabezpieczeń nie powinien opierać się na kodzie przezroczystym do wykonywania pełnego żądania. Każdy kod, który wykonuje kontrole zabezpieczeń, na przykład wymagania dotyczące zabezpieczeń, powinien być w zamian bezpieczny-krytyczny.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ogólnie rzecz biorąc, aby naprawić naruszenie tej zasady, oznacz metodę <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem. Możesz również usunąć żądanie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Pliki reguł w następującym kodzie, ponieważ metoda przezroczysta powoduje deklaratywne zapotrzebowanie na zabezpieczenia.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>Zobacz też
 [CA2142: Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
