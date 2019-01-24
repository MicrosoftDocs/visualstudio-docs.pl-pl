---
title: 'CA2119: Pieczętuj metody, które spełniają wymagania interfejsów prywatnych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6768bb0100b3bb0052898efc6a57017fca3702b9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754765"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Pieczętuj metody, które spełniają wymagania interfejsów prywatnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Dziedziczny typ publiczny dostarcza zastępowalną implementację metody `internal` (`Friend` w języku Visual Basic) interfejsu.

## <a name="rule-description"></a>Opis reguły
 Metody interfejsu muszą powszechnej dostępności, której nie można zmienić w typie implementującym. Interfejs wewnętrzny tworzy kontraktu, który nie jest przeznaczony do implementacji spoza zestawu, który definiuje interfejs. Publiczny typ, który implementuje metodę interfejsu wewnętrznego przy użyciu `virtual` (`Overridable` w języku Visual Basic) modyfikator umożliwia metody do zastąpienia przez typ pochodny, który znajduje się poza zestaw. Jeśli drugi typ w zestawie definiujące wywołuje metodę i oczekuje, że kontrakt wyłącznie wewnętrznym, zachowanie jest zagrożona podczas zamiast tego przesłonięte metody w zestawie poza jest wykonywany. Spowoduje to utworzenie luki w zabezpieczeniach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zapobiegania metody zastępowaniu spoza zestawu przy użyciu jednej z następujących czynności:

-   Zmień typ deklarujący `sealed` (`NotInheritable` w języku Visual Basic).

-   Zmień dostępność elementu typ deklarujący `internal` (`Friend` w języku Visual Basic).

-   Usuń wszystkich konstruktorów publicznych z typ deklarujący.

-   Implementuje metody bez używania `virtual` modyfikator.

-   Jawnie implementować metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Bezpiecznie ostrzeżenia z tej reguły, jeśli po dokładnej przeglądu żadnych problemów z zabezpieczeniami istnieją, które może być możliwe, jeśli metoda zostanie przesłonięta spoza zestawu.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu `BaseImplementation`, który narusza tę regułę.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Przykład
 Poniższy przykład wykorzystuje metodę wirtualną wykonania poprzedniego przykładu.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Zobacz też
 [Interfejsy](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [interfejsów](http://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)
