---
title: 'CA1500: nazwy zmiennych nie powinny odpowiadać nazwom pól | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b46594a53e6562c2c6a069a9a25d58b3e32865eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607940"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1500: nazwy zmiennych nie powinny odpowiadać nazwom pól](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names).

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Kategoria|Microsoft. łatwość obsługi|
|Zmiana kluczowa|Gdy jest uruchamiany na parametrze, który ma taką samą nazwę jak pole:<br /><br /> -Bez przerywania — Jeśli zarówno pole, jak i Metoda deklarująca parametr nie mogą być widoczne poza zestawem, niezależnie od wprowadzonej zmiany.<br />-Dzielenie — Jeśli zmienisz nazwę pola i będzie można je zobaczyć poza zestawem.<br />-Przerywanie — Jeśli zmienisz nazwę parametru i metodę, która deklaruje, może być widoczna poza zestawem.<br /><br /> Gdy jest uruchamiany w zmiennej lokalnej, która ma taką samą nazwę jak pole:<br /><br /> -Bez przerywania — Jeśli pole nie może być widoczne poza zestawem, niezależnie od wprowadzonej zmiany.<br />-Bez przerywania — Jeśli zmienisz nazwę zmiennej lokalnej i nie zmienisz nazwy pola.<br />-Dzielenie — Jeśli zmienisz nazwę pola i będzie ono widoczne poza zestawem.|

## <a name="cause"></a>Przyczyna
 Metoda wystąpienia deklaruje parametr lub zmienną lokalną, której nazwa pasuje do pola wystąpienia typu deklarującego. Aby przechwytywać lokalne zmienne naruszające regułę, testowany zestaw musi być skompilowany przy użyciu informacji debugowania, a plik bazy danych programu (. pdb) musi być dostępny.

## <a name="rule-description"></a>Opis reguły
 Gdy nazwa pola wystąpienia pasuje do parametru lub nazwy zmiennej lokalnej, do pola wystąpienia uzyskuje się dostęp za pomocą słowa kluczowego `this` (`Me` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), gdy jest wewnątrz treści metody. Podczas zachowywania kodu można łatwo zapomnieć o tej różnicy i założyć, że zmienna parametru/Local odwołuje się do pola wystąpienia, które prowadzi do błędów. Dotyczy to szczególnie długich treści metod.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień nazwę parametru/zmiennej lub pola.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono dwa naruszenia reguły.

 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
