---
title: 'CA1810: Inicjowanie pola statyczne typu referencyjnego śródwierszowo | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 709efb61faa21bb914a9622a7fdb65e2775b6a4e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893576"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicjowanie pola statyczne typu referencyjnego śródwierszowo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ odwołania deklaruje jawny, statyczny Konstruktor.

## <a name="rule-description"></a>Opis reguły
 Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Inicjowanie statyczne są wyzwalane podczas uzyskiwania dostępu do dowolnego członka statycznego lub gdy tworzone jest wystąpienie tego typu. Jednak statyczne inicjowanie nie jest wyzwalany, jeśli zadeklarować zmienną typu, ale nie należy jej używać, które mogą być ważne, jeśli inicjowanie zmieni się stan globalny.

 Gdy wszystkie dane statyczne są wbudowane zainicjowane i jawny, statyczny Konstruktor nie jest zadeklarowana, Kompilatory języka intermediate language (MSIL) firmy Microsoft, Dodaj `beforefieldinit` flagę i niejawne Konstruktor statyczny, który inicjuje danych statycznych, typowi MSIL Definicja. Kiedy kompilator JIT napotka `beforefieldinit` Flaga w większości przypadków sprawdzenia konstruktora statycznego nie zostały dodane. Statyczne inicjowanie może wystąpić na pewien czas, zanim wszystkie pola statyczne są dostępne, ale nie, przed wywołaniem konstruktora statycznej metody lub wystąpienia. Należy pamiętać, że Inicjowanie statyczne mogą występować w dowolnej chwili po zadeklarowaniu zmiennej o typie.

 Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. Często statyczny Konstruktor jest używana tylko do zainicjowania pola statyczne, w których przypadku musisz tylko upewnić się, że inicjowanie statycznych występuje przed pierwszym dostępie pole statyczne. `beforefieldinit` Zachowanie jest odpowiednia dla tych i innych typów. Jest tylko nieodpowiednie, gdy statyczne inicjowanie ma wpływ na stan globalny jest spełniony jeden z następujących czynności:

-   Wpływ na stan globalny jest kosztowne, a nie jest wymagane, jeśli typ nie jest używany.

-   Efekty stan globalny jest możliwy bez uzyskiwania dostępu do dowolnego pola statyczne typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne pominąć ostrzeżenie od tej reguły, jeśli wydajność nie ma znaczenia; lub jeśli stan globalny zmiany, które są spowodowane przez statyczne inicjowanie są kosztowne musi można zagwarantować przed statycznej metody tego typu jest nazywany lub tworzone jest wystąpienie tego typu.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typem `StaticConstructor`, który narusza regułę i typu `NoStaticConstructor`, który zamienia statyczny Konstruktor inicjalizacji wbudowane spełniają reguły.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Należy pamiętać, dodanie `beforefieldinit` Flaga w definicji MSIL dla `NoStaticConstructor` klasy.

 **.klasa publicznych auto ansi StaticConstructor** **rozszerza [mscorlib]System.Object**
 **{**
 **} / / koniec klasy StaticConstructor** 
 **.klasa publicznych automatycznie ansi beforefieldinit NoStaticConstructor** **rozszerza [mscorlib]System.Object**
 **{** 
 **} / / koniec klasy NoStaticConstructor**
## <a name="related-rules"></a>Powiązane reguły
 [CA2207: Typu wartości Inicjuj pola statyczne bezpośrednio](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
