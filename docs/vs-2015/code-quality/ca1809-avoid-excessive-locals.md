---
title: 'CA1809: Unikaj nadmiernych ustawień lokalnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d39c8d9d09cf457738df87e3c2e6e109f7bc1696
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543861"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Unikaj zbyt wielu zmiennych lokalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategoria|Microsoft. Performance|
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
 [CA1804: Usuwaj nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)
