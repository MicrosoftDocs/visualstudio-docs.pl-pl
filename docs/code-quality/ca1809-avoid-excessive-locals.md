---
title: 'CA1809: Unikaj zbyt wielu zmiennych lokalnych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0824517aa7d5dc05f9a0297ca44cd235f5800653
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904020"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Unikaj zbyt wielu zmiennych lokalnych

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Element członkowski zawiera więcej niż 64 zmienne lokalne, niektóre z nich mogą być generowane przez kompilator.

## <a name="rule-description"></a>Opis reguły
 Typowa Optymalizacja wydajności jest do przechowywania wartości w rejestrze procesora zamiast w pamięci, co jest nazywane *rejestrowanie* wartość. Środowisko uruchomieniowe języka wspólnego uwzględnia maksymalnie 64 zmienne lokalne dla enregistration. Zmienne, które nie są przechowywane w rejestrze procesora są umieszczane na stosie i należy przenieść do rejestru przed manipulacji. Aby zezwolić na ryzyko, wszystkie zmienne lokalne uzyskać przechowywane w rejestrze procesora, ograniczyć liczbę zmiennych lokalnych do 64.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, refaktoryzować implementacji, aby używać nie więcej niż 64 zmienne lokalne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne, aby pominąć ostrzeżenie od tej reguły lub wyłączyć regułę, jeśli wydajność nie ma problemu.

## <a name="related-rules"></a>Powiązane reguły
 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)