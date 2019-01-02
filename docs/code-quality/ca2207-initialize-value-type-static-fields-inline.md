---
title: 'CA2207: Typu wartości Inicjuj pola statyczne bezpośrednio'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee4ffd51eef5b8a4f0523dd2356d4e0bdb29b945
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869164"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Typu wartości Inicjuj pola statyczne bezpośrednio

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ wartości deklaruje jawny, statyczny Konstruktor.

## <a name="rule-description"></a>Opis reguły
 Gdy typ wartości jest zadeklarowany, wewnętrzny ulega inicjowanie domyślne, gdzie wszystkie pola typu wartości są ustawione na zero, a wszystkie pola typu odwołania są ustawione na `null` (`Nothing` w języku Visual Basic). Jawny, statyczny Konstruktor tylko jest gwarantowane do uruchomienia przed w konstruktorze wystąpienia lub statyczną składową typu jest wywoływana. W związku z tym jeśli typ jest tworzony bez wywoływania konstruktora wystąpienia, Konstruktor statyczny nie jest gwarantowane do uruchomienia.

 Jeśli wszystkie dane statyczne są wbudowane zainicjowane, a nie jawny, statyczny Konstruktor jest zadeklarowany, Kompilatory języka C# i Visual Basic Dodaj `beforefieldinit` flagi do definicji klasy MSIL. Kompilatory również dodać Konstruktor statyczny prywatny, zawierający kod inicjowania statycznych. Ten konstruktor statyczny prywatny jest gwarantowane, zanim wszystkie pola statyczne typu są dostępne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady Zainicjuj wszystkie dane statyczne, gdy jest zadeklarowany i Usuń Konstruktor statyczny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1810: Inicjowanie pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)