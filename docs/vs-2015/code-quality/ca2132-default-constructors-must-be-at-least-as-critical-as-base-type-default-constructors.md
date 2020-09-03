---
title: 'CA2132: konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 401aa6f5ebec4dac99bedba6f12478c7c48d1dc5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540819"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

> [!NOTE]
> To ostrzeżenie jest stosowane tylko do kodu, na którym działa CoreCLR (wersja środowiska CLR, która jest specyficzna dla aplikacji sieci Web Silverlight).

## <a name="cause"></a>Przyczyna
 Atrybut przezroczystości domyślnego konstruktora klasy pochodnej nie jest tak krytyczny jak przezroczystość klasy bazowej.

## <a name="rule-description"></a>Opis reguły
 Typy i elementy członkowskie, które mają <xref:System.Security.SecurityCriticalAttribute> nie mogą być używane przez kod aplikacji Silverlight. Krytyczne dla bezpieczeństwa typy i składowe mogą być używane tylko przez zaufany kod w środowisku .NET Framework dla biblioteki klas Silverlight. Ze względu na to, że publiczna lub chroniona konstrukcja w klasie pochodnej musi mieć taką samą lub większą przejrzystość jak jej klasa bazowa, klasy w aplikacji nie mogą pochodzić z klasy oznaczonej jako SecurityCritical.

 W przypadku kodu platformy CoreCLR, jeśli typ podstawowy ma publiczny lub chroniony nieprzezroczysty Konstruktor domyślny, typ pochodny musi przestrzegać reguł dziedziczenia konstruktora domyślnego. Typ pochodny musi również mieć konstruktora domyślnego i ten konstruktor musi być co najmniej jako krytyczny domyślny Konstruktor typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie, Usuń typ lub nie pochodzą od zabezpieczeń nieprzezroczystego typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń z tej reguły. Naruszenia tej reguły przez kod aplikacji spowodują odmowę załadowania typu za pomocą elementu CoreCLR <xref:System.TypeLoadException> .

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Komentarze
