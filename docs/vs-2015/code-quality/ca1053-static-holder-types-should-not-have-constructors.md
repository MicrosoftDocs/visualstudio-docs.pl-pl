---
title: 'CA1053: statyczne typy posiadaczy nie powinny mieć konstruktorów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7de098d264dbdd6d7d9daea385de2e03d4e1ba35
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653821"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Typy obsługi statycznej nie powinny mieć konstruktorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub publiczny zagnieżdżony deklaruje tylko statyczne elementy członkowskie i ma publiczny lub chroniony konstruktor domyślny.

## <a name="rule-description"></a>Opis reguły
 Konstruktor jest zbędny, ponieważ wywołanie statycznego elementu członkowskiego nie wymaga wystąpienia tego typu. Ponadto, ponieważ typ nie ma elementów członkowskich niestatycznych, utworzenie wystąpienia nie zapewnia dostępu do żadnego z elementów członkowskich typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Usuń Konstruktor domyślny lub ustaw go jako prywatny.

> [!NOTE]
> Niektóre kompilatory automatycznie tworzą publiczny Konstruktor domyślny, jeśli typ nie definiuje żadnych konstruktorów. Jeśli jest to przypadek z typem, Dodaj prywatny Konstruktor domyślny, aby wyeliminować naruszenie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Obecność konstruktora sugeruje, że typ nie jest typem statycznym.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę. Zwróć uwagę, że w kodzie źródłowym nie ma domyślnego konstruktora. Gdy ten kod jest kompilowany do zestawu, C# kompilator wstawi Konstruktor domyślny, który będzie naruszał tę regułę. Aby rozwiązać ten konieczność, zadeklaruj konstruktora prywatnego.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
