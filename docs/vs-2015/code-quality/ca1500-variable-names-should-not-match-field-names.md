---
title: 'CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8dc15c95398ed45954c3830d1c558a6653a4346f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191489"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Nazwy zmiennych nie powinny być zgodne z nazwami pól
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1500: Nazwy zmiennych nie powinny odpowiadać nazwom pól](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names).  
  
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|Kategoria|Microsoft.Maintainability|  
|Zmiana kluczowa|Gdy wywoływane na parametr, który ma taką samą nazwę jako pola:<br /><br /> Niepowodujących niezgodności — Jeśli nie są widoczne pola i metody, która deklaruje parametr spoza zestawu, niezależnie od tego, wprowadzone zmiany.<br />-Istotne - po zmianie nazwy pola i są widoczne poza zestawem.<br />-Istotne — Jeśli zmienisz nazwę parametru i metody, która deklaruje ją są widoczne poza zestawem.<br /><br /> Gdy wywoływane na zmiennej lokalnej, która ma taką samą nazwę jako pola:<br /><br /> Niepowodujących niezgodności — Jeśli pola nie są widoczne spoza zestawu, niezależnie od tego, wprowadzone zmiany.<br />Niepowodujących niezgodności — Jeśli zmiana nazwy zmiennej lokalnej, a nie zmieniaj nazwy pola.<br />-Istotne — Jeśli zmieniasz nazwę pola i może być widoczny spoza zestawu.|  
  
## <a name="cause"></a>Przyczyna  
 Metoda wystąpienia deklaruje parametr lub zmienna lokalna, których nazwa pasuje do pola wystąpienia typu deklarującego. Aby przechwytywać zmienne lokalne, które naruszają reguły, przetestowane zestawu muszą zostać skompilowane przy użyciu informacji o debugowaniu i plik bazy danych (PDB) programu skojarzone muszą być dostępne.  
  
## <a name="rule-description"></a>Opis reguły  
 Jeśli nazwa pola wystąpienia jest zgodna, parametr lub nazwę zmiennej lokalnej, pole wystąpienia odbywa się za pomocą `this` (`Me` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) — słowo kluczowe, gdy komputer znajduje się wewnątrz treści metody. Utrzymywanie kodu, jest łatwo zapomnieć ta różnica i przyjęto założenie, że zmienna parametr/elementu lokalnego odwołuje się do pola wystąpienia, co prowadzi do błędów. Dotyczy to zwłaszcza treści metod długiej.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, Zmień nazwę parametru/zmiennej lub pola.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia dwa naruszenia reguły.  
  
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
