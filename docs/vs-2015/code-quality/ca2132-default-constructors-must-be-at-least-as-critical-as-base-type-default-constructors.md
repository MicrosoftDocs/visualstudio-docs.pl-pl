---
title: 'CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8287fdf4c767e6fc2a41f014f724ab9a7fe61249
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385832"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

> [!NOTE]
> To ostrzeżenie jest stosowane tylko do kodu, który jest uruchomiony w środowisku CoreCLR (wersja środowiska CLR, które są specyficzne dla aplikacji sieci Web w technologii Silverlight).

## <a name="cause"></a>Przyczyna
 Atrybut przezroczystości pod względem konstruktora domyślnego w klasie pochodnej nie jest tak krytyczny, jak przezroczystość klasy bazowej.

## <a name="rule-description"></a>Opis reguły
 Typy i elementy członkowskie, które mają <xref:System.Security.SecurityCriticalAttribute> nie może być używany przez kod aplikacji Silverlight. Krytyczne dla bezpieczeństwa typy i składowe mogą być używane tylko przez zaufany kod w środowisku .NET Framework dla biblioteki klas Silverlight. Ze względu na to, że publiczna lub chroniona konstrukcja w klasie pochodnej musi mieć taką samą lub większą przejrzystość jak jej klasa bazowa, klasy w aplikacji nie mogą pochodzić z klasy oznaczonej jako SecurityCritical.

 Dla kodu platformy CoreCLR Jeśli typ podstawowy ma publiczny lub chroniony nieprzezroczyste domyślnego konstruktora następnie Typ pochodny musi przestrzegać zasady dziedziczenia Konstruktor domyślny. Typ pochodny również musi mieć konstruktora domyślnego i tego konstruktora musi wynosić co najmniej jako krytyczne domyślny konstruktor obiektu typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie, Usuń typ lub pochodzi z zabezpieczenia-przejrzysty.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń od tej reguły. Naruszenie tej zasady przez kod aplikacji spowoduje CoreCLR odmowy można załadować typu o <xref:System.TypeLoadException>.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Komentarze
