---
title: 'CA2114: Zabezpieczenie metody powinno być nadzbiorem typu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 623416e557759ace1ad6403ef8ef977df01da39e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911133"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Zabezpieczenie metody powinno być nadzbiorem typu

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ ma zabezpieczenia deklaratywne, jeden z jego metody ma zabezpieczenia deklaratywne dla tego samego działania zabezpieczeń i akcji zabezpieczeń nie jest [zapotrzebowania na łącza](/dotnet/framework/misc/link-demands), i uprawnienia sprawdzana przez typ nie są podzbiorem uprawnienia sprawdzane przez metodę.

## <a name="rule-description"></a>Opis reguły
 Metoda nie powinna mieć zarówno metody typu poziomie i zabezpieczenia deklaratywne dla tego samego działania. Dwa testy nie są połączone; dotyczy tylko żądanie poziom metody. Na przykład, jeśli typem zażąda uprawnień `X`, oraz jednej z jego metod zażąda uprawnień `Y`, kod nie musi mieć uprawnienie `X` wykonania metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Przejrzyj kod, aby upewnić się, że wymagane są obie akcje. Jeśli wymagane są obie akcje, upewnij się, że czynność na poziomie obejmuje zabezpieczeń określone na poziomie typu. Na przykład, jeśli danego typu zażąda uprawnień `X`, i jej metodę także musi żądać uprawnienia `Y`, metoda jawnie zażądać `X` i `Y`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli metoda nie wymaga zabezpieczeń określone przez typ. Jednak to nie jest to zwykła scenariusz i mogą wskazywać na potrzeby przeglądu zachowania ostrożności podczas projektowania.

## <a name="example-1"></a>Przykład 1

W poniższym przykładzie użyto uprawnienia dotyczące środowiska, aby zademonstrować niebezpieczeństwa naruszenie tej zasady. W tym przykładzie kodu aplikacji tworzy wystąpienia typu zabezpieczonego, zanim nastąpi odmowa uprawnień wymaganych przez typ. W przypadku rzeczywistych zagrożeń aplikacja będzie wymagać innym sposobem na uzyskanie wystąpienia obiektu.

W poniższym przykładzie zapotrzebowanie biblioteki uprawnienia dla typu zapisu i uprawnienia dla metody do odczytu.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Przykład 2

Poniższy kod aplikacji przedstawia luk w zabezpieczeniach biblioteki przez wywołanie metody, nawet jeśli nie spełnia on wymagania zabezpieczeń na poziomie typu.

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Zapotrzebowanie na łącza](/dotnet/framework/misc/link-demands)
- [Dane i modelowanie](/dotnet/framework/data/index)