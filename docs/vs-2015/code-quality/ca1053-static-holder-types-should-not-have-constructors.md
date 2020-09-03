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
ms.openlocfilehash: 29cc322dd59dc0de66af8f92a46524d15b0022c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539584"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
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
 Poniższy przykład pokazuje typ, który narusza tę regułę. Zwróć uwagę, że w kodzie źródłowym nie ma domyślnego konstruktora. Gdy ten kod jest kompilowany do zestawu, kompilator języka C# wstawi Konstruktor domyślny, który będzie naruszał tę regułę. Aby rozwiązać ten konieczność, zadeklaruj konstruktora prywatnego.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
