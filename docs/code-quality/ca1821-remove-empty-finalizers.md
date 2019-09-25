---
title: 'CA1821: Usuwaj puste finalizatory'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a93ebea78c9258667d7c6ca10e35d22fc4113f48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233443"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Usuwaj puste finalizatory

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Kategoria|Microsoft.Performance|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ implementuje finalizator, który jest pusty, wywołuje tylko finalizator typu podstawowego lub wywołuje tylko metody, które są emitowane warunkowo.

## <a name="rule-description"></a>Opis reguły

W każdym przypadku można unikać finalizatorów z powodu dodatkowych obciążeń związanych z wydajnością, które są związane ze śledzeniem okresu istnienia obiektu. Moduł wyrzucania elementów bezużytecznych uruchamia finalizator przed zebraniem obiektu. Oznacza to, że co najmniej dwie kolekcje są wymagane do zebrania obiektu. Pusty finalizator wiąże się z tym dodatkowym obciążeniem bez żadnej korzyści.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Usuń pusty finalizator. Jeśli finalizator jest wymagany do debugowania, należy ująć cały finalizator w `#if DEBUG / #endif` dyrektywy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj komunikatu z tej reguły.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono pusty finalizator, który powinien zostać usunięty, finalizator, który powinien być ujęty w `#if DEBUG / #endif` dyrektywy, i finalizator, który poprawnie `#if DEBUG / #endif` używa dyrektyw.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]
