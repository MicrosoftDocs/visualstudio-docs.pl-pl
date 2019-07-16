---
title: 'CA2143: Metody przezroczyste nie powinny używać żądań zabezpieczeń | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5f9983f832c8793140f79e9b835e26e44fae1927
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142677"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Metody przezroczyste nie powinny używać żądań zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Przezroczystym typ lub metoda deklaratywne jest oznaczona za pomocą <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` żądanie lub wywołania metody <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> metody.

## <a name="rule-description"></a>Opis reguły
 Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Przejrzysty pod względem bezpieczeństwa kod powinien używać pełnych żądań do podejmowania decyzji związanych z zabezpieczeniami, a kod krytyczny pod względem zabezpieczeń nie powinien opierać się na kodzie przezroczystym do wykonywania pełnego żądania. Zamiast tego powinien być bezpieczny krytyczny wszelki kod, który wykonuje sprawdzanie zabezpieczeń, takich jak wymogów bezpieczeństwa.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Ogólnie rzecz biorąc, aby naprawić naruszenie tej zasady, należy oznaczyć metody <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu. Można również usunąć żądanie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Reguła pliki na następujący kod, ponieważ metoda przezroczysta pod względem sprawia, że żądanie zabezpieczeń deklaratywnych.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>Zobacz też
 [CA2142: Przezroczysty kod nie powinien być chroniony za pomocą żądań Linkdemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
