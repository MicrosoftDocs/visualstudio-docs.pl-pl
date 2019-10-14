---
title: 'CA2207: Pola statyczne typu wartości inicjuj bezpośrednio'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 695f15c73120f766157fabb09193d32115dda588
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305933"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Pola statyczne typu wartości inicjuj bezpośrednio

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Category|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ wartości deklaruje jawny Konstruktor statyczny.

## <a name="rule-description"></a>Opis reguły
Gdy typ wartości jest zadeklarowany, zostanie on przekierowany do domyślnej inicjalizacji, w której wszystkie pola typu wartości są ustawione na zero, a wszystkie pola typu odwołania są ustawione na `null` (`Nothing` w Visual Basic). Jawny Konstruktor statyczny gwarantuje tylko uruchomienie przed wywołaniem konstruktora wystąpienia lub statycznego elementu członkowskiego typu. W związku z tym, jeśli typ jest tworzony bez wywoływania konstruktora wystąpienia, Konstruktor statyczny nie jest gwarantowany do uruchomienia.

Jeśli wszystkie dane statyczne są inicjowane wewnętrznie i nie zadeklarowano jawnego konstruktora statycznego, kompilatory C# i Visual Basic dodają flagę `beforefieldinit` do definicji klasy MSIL. Kompilatory dodają również prywatny statyczny Konstruktor zawierający kod inicjalizacji statycznej. Ten prywatny statyczny Konstruktor jest gwarantowany do uruchomienia przed uzyskaniem dostępu do dowolnych pól statycznych typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, zainicjuj wszystkie dane statyczne, gdy jest zadeklarowana, i Usuń Konstruktor statyczny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły
[CA1810: Inicjuj wbudowane pola typu odwołania @ no__t-0