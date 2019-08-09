---
title: 'CA1809: Unikaj zbyt wielu zmiennych lokalnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d1c2f76258be3b0be6409bffd002fd916883ab2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921535"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Unikaj zbyt wielu zmiennych lokalnych

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Element członkowski zawiera więcej niż 64 zmiennych lokalnych, z których część może być wygenerowana przez kompilator.

## <a name="rule-description"></a>Opis reguły
Typowym optymalizacją wydajności jest przechowywanie wartości w rejestrze procesora zamiast w pamięci, która jest określana jako *Rejestrowanie* wartość. Środowisko uruchomieniowe języka wspólnego traktuje do 64 zmiennych lokalnych dla enregistration. Zmienne, które nie są przechowywane są umieszczane na stosie i muszą zostać przeniesione do rejestru przed manipulacją. Aby zezwolić na szansę, że wszystkie zmienne lokalne uzyskują przechowywane, Ogranicz liczbę zmiennych lokalnych do 64.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Refaktoryzacja implementacji do użycia nie więcej niż 64 zmiennych lokalnych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Istnieje możliwość bezpiecznego pomijania ostrzeżenia z tej reguły lub wyłączenia reguły, jeśli wydajność nie jest problemem.

## <a name="related-rules"></a>Powiązane reguły
[CA1804: Usuń nieużywane elementy lokalne](../code-quality/ca1804-remove-unused-locals.md)