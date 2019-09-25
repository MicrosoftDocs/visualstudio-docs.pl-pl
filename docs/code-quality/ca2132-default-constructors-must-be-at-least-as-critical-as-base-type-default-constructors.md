---
title: 'CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c5ca98219444515d01baf670489120238cb8dda
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232330"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

> [!NOTE]
> To ostrzeżenie jest stosowane tylko do kodu, na którym działa CoreCLR (wersja środowiska CLR, która jest specyficzna dla aplikacji sieci Web Silverlight).

## <a name="cause"></a>Przyczyna

Atrybut przezroczystości domyślnego konstruktora klasy pochodnej nie jest tak krytyczny jak przezroczystość klasy bazowej.

## <a name="rule-description"></a>Opis reguły

Typy i elementy członkowskie, które <xref:System.Security.SecurityCriticalAttribute> mają nie mogą być używane przez kod aplikacji Silverlight. Krytyczne dla bezpieczeństwa typy i składowe mogą być używane tylko przez zaufany kod w środowisku .NET Framework dla biblioteki klas Silverlight. Ze względu na to, że publiczna lub chroniona konstrukcja w klasie pochodnej musi mieć taką samą lub większą przejrzystość jak jej klasa bazowa, klasy w aplikacji nie mogą pochodzić z klasy oznaczonej jako SecurityCritical.

W przypadku kodu platformy CoreCLR, jeśli typ podstawowy ma publiczny lub chroniony nieprzezroczysty Konstruktor domyślny, typ pochodny musi przestrzegać reguł dziedziczenia konstruktora domyślnego. Typ pochodny musi również mieć konstruktora domyślnego i ten konstruktor musi być co najmniej jako krytyczny domyślny Konstruktor typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie, Usuń typ lub nie pochodzą od zabezpieczeń nieprzezroczystego typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń z tej reguły. Naruszenia tej reguły przez kod aplikacji spowodują odmowę załadowania typu za pomocą elementu <xref:System.TypeLoadException>CoreCLR.

### <a name="code"></a>Kod

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]