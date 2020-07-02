---
title: 'CA2114: zabezpieczenia metody muszą być nadzbiorem typu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d7879d8b2aa9eb4ece1ce07f89681b6c0b0f5f31
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534709"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Zabezpieczenie metody powinno być nadzbiorem typu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ ma Zabezpieczenia deklaracyjne, a jedna z jej metod ma deklaracyjne zabezpieczenia dla tej samej akcji zabezpieczeń, a akcja zabezpieczeń nie jest zgodna z [wymaganiami](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) lub [dziedziczeniem](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9), a uprawnienia sprawdzane przez typ nie są podzbiorem uprawnień sprawdzanych przez metodę.

## <a name="rule-description"></a>Opis reguły
 Metoda nie powinna mieć zarówno zabezpieczeń deklaratywnych na poziomie metody, jak i na poziomie typu dla tej samej akcji. Dwa kontrole nie są połączone; stosowane jest tylko żądanie na poziomie metody. Na przykład, jeśli typ wymaga uprawnień `X` , a jedna z jej metod wymaga uprawnień `Y` , kod nie musi mieć uprawnienia `X` do wykonywania metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Sprawdź swój kod, aby upewnić się, że obie akcje są wymagane. Jeśli wymagane są obie akcje, upewnij się, że akcja na poziomie metody obejmuje zabezpieczenia określone na poziomie typu. Na przykład, jeśli typ wymaga uprawnień `X` , a jego Metoda musi również mieć uprawnienia żądanie `Y` , metoda powinna jawnie wymagać `X` i `Y` .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli metoda nie wymaga zabezpieczeń określonych przez typ, bezpieczniej jest pominąć ostrzeżenie z tej reguły. Nie jest to jednak zwykły scenariusz i może wskazywać potrzebę dokładnego przeglądu projektu.

## <a name="example"></a>Przykład
 W poniższym przykładzie zastosowano uprawnienia środowiska w celu zademonstrowania zagrożeń naruszających tę regułę. W tym przykładzie kod aplikacji tworzy wystąpienie zabezpieczonego typu przed odmową uprawnienia wymaganego przez typ. W rzeczywistym scenariuszu zagrożeń aplikacja będzie wymagać innego sposobu uzyskania wystąpienia obiektu.

 W poniższym przykładzie biblioteka wymaga uprawnień do zapisu dla typu i uprawnienia do odczytu dla metody.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Przykład
 Poniższy kod aplikacji demonstruje lukę w zabezpieczeniach biblioteki, wywołując metodę, mimo że nie spełnia wymagań zabezpieczeń na poziomie typu.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **[Wszystkie uprawnienia] informacje osobiste: 6/16/1964 12:00:00 am** 
 **[Brak uprawnień do zapisu (na żądanie według typu)] informacje osobiste: 6/16/1964 12:00:00 am** 
 **[Brak uprawnienia do odczytu (żądanie)] nie można uzyskać dostępu do informacji osobistych: żądanie nie powiodło się.**
## <a name="see-also"></a>Zobacz też
 [Zasady bezpiecznego kodowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) — [wymagania dziedziczenia](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [żądania](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [danych i modelowania](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
