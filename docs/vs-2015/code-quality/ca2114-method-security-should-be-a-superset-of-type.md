---
title: 'CA2114: Zabezpieczenie metody powinno być nadzbiorem typu | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9e0024ae6db5af3f1cf23c07fe29fbac8e4827d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788892"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Zabezpieczenie metody powinno być nadzbiorem typu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ ma zabezpieczenia deklaratywne, jeden z jego metody ma zabezpieczenia deklaratywne dla tego samego działania zabezpieczeń i akcji zabezpieczeń nie jest [zapotrzebowania na łącza](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) lub [Inheritancedemand](http://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)oraz uprawnienia sprawdzany przez typ nie są podzbiorem uprawnienia metodę.

## <a name="rule-description"></a>Opis reguły
 Metoda nie powinna mieć zarówno metody typu poziomie i zabezpieczenia deklaratywne dla tego samego działania. Dwa testy nie są połączone; dotyczy tylko żądanie poziom metody. Na przykład, jeśli typem zażąda uprawnień `X`, oraz jednej z jego metod zażąda uprawnień `Y`, kod nie musi mieć uprawnienie `X` wykonania metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Przejrzyj kod, aby upewnić się, że wymagane są obie akcje. Jeśli wymagane są obie akcje, upewnij się, że czynność na poziomie obejmuje zabezpieczeń określone na poziomie typu. Na przykład, jeśli danego typu zażąda uprawnień `X`, i jej metodę także musi żądać uprawnienia `Y`, metoda jawnie zażądać `X` i `Y`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli metoda nie wymaga zabezpieczeń określone przez typ. Jednak to nie jest to zwykła scenariusz i mogą wskazywać na potrzeby przeglądu zachowania ostrożności podczas projektowania.

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto uprawnienia dotyczące środowiska, aby zademonstrować niebezpieczeństwa naruszenie tej zasady. W tym przykładzie kodu aplikacji tworzy wystąpienia typu zabezpieczonego, zanim nastąpi odmowa uprawnień wymaganych przez typ. W przypadku rzeczywistych zagrożeń aplikacja będzie wymagać innym sposobem na uzyskanie wystąpienia obiektu.

 W poniższym przykładzie zapotrzebowanie biblioteki uprawnienia dla typu zapisu i uprawnienia dla metody do odczytu.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Przykład
 Poniższy kod aplikacji przedstawia luk w zabezpieczeniach biblioteki przez wywołanie metody, nawet jeśli nie spełnia on wymagania zabezpieczeń na poziomie typu.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **[Wszystkie uprawnienia] Informacje osobiste: 6/16/1964 12:00:00 AM**
 **[ma uprawnienia do zapisu (wymagane przez typ)] informacje osobiste: 6/16/1964 12:00:00 AM**
 **[nie uprawnień do odczytu (wymagany przez metodę)] można uzyskać dostępu do informacji osobistych: Żądanie nie powiodło się.**
## <a name="see-also"></a>Zobacz też
 [Wytyczne dotyczące bezpiecznego programowania](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Inheritancedemand](http://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [Link zapotrzebowanie](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [dane i modelowanie](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
