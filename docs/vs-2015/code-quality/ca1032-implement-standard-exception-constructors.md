---
title: 'CA1032: Zaimplementuj standardowe konstruktory wyjątków | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 61b0157200ddff4cb8335118b30832a0c8950f65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542288"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Zaimplementuj standardowe konstruktory wyjątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ rozszerza <xref:System.Exception?displayProperty=fullName> i nie deklaruje wszystkich wymaganych konstruktorów.

## <a name="rule-description"></a>Opis reguły
 Typy wyjątków muszą implementować następujące konstruktory:

- Public NewException ()

- Public NewException (ciąg)

- Public NewException (ciąg, wyjątek)

- chroniona lub prywatna NewException (SerializationInfo, StreamingContext)

  Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków. Na przykład Konstruktor, który ma sygnaturę, `NewException(string, Exception)` jest używany do tworzenia wyjątków, które są spowodowane innymi wyjątkami. Bez tego konstruktora nie można utworzyć i zgłosić wystąpienia wyjątku niestandardowego, który zawiera wewnętrzny (zagnieżdżony) wyjątek, który jest tym, jaki kod zarządzany powinien wykonać w takiej sytuacji. Pierwsze trzy konstruktory wyjątków są publiczne według Konwencji. Czwarty Konstruktor jest chroniony w niezapieczętowanych klasach i prywatny w klasach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [CA2229: Implementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj brakujące konstruktory do wyjątku i upewnij się, że mają one poprawną dostępność.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy naruszenie jest spowodowane przez użycie innego poziomu dostępu dla konstruktorów publicznych.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera typ wyjątku, który narusza tę regułę i typ wyjątku, który jest poprawnie zaimplementowany.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
