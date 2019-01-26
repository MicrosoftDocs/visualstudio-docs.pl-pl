---
title: 'CA1500: Nazwy zmiennych nie powinny być zgodne z nazwami pól'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 56deb12f98767a62aed55f4e979ff666200ea044
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995144"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Nazwy zmiennych nie powinny być zgodne z nazwami pól

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Gdy wywoływane na parametr, który ma taką samą nazwę jako pola:<br /><br /> Niepowodujących niezgodności — Jeśli nie są widoczne pola i metody, która deklaruje parametr spoza zestawu, niezależnie od tego, wprowadzone zmiany.<br />-Istotne - po zmianie nazwy pola i są widoczne poza zestawem.<br />-Istotne — Jeśli zmienisz nazwę parametru i metody, która deklaruje ją są widoczne poza zestawem.<br /><br /> Gdy wywoływane na zmiennej lokalnej, która ma taką samą nazwę jako pola:<br /><br /> Niepowodujących niezgodności — Jeśli pola nie są widoczne spoza zestawu, niezależnie od tego, wprowadzone zmiany.<br />Niepowodujących niezgodności — Jeśli zmiana nazwy zmiennej lokalnej, a nie zmieniaj nazwy pola.<br />-Istotne — Jeśli zmieniasz nazwę pola i może być widoczny spoza zestawu.|

## <a name="cause"></a>Przyczyna

Metoda wystąpienia deklaruje parametr lub zmienna lokalna, których nazwa pasuje do pola wystąpienia typu deklarującego. Aby przechwytywać zmienne lokalne, które naruszają reguły, przetestowane zestawu muszą zostać skompilowane przy użyciu informacji o debugowaniu i plik bazy danych (PDB) programu skojarzone muszą być dostępne.

## <a name="rule-description"></a>Opis reguły

Jeśli nazwa pola wystąpienia jest zgodna, parametr lub nazwę zmiennej lokalnej, pole wystąpienia odbywa się za pomocą `this` (`Me` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) — słowo kluczowe, gdy komputer znajduje się wewnątrz treści metody. Utrzymywanie kodu, jest łatwo zapomnieć ta różnica i przyjęto założenie, że zmienna parametr/elementu lokalnego odwołuje się do pola wystąpienia, co prowadzi do błędów. Dotyczy to zwłaszcza treści metod długiej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Zmień nazwę parametru/zmiennej lub pola.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia dwa naruszenia reguły.

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]