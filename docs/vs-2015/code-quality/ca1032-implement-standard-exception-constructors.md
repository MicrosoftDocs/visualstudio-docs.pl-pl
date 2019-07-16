---
title: 'CA1032: Zaimplementuj standardowe konstruktory wyjątku | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c59da56304a5d1d8f2cca7eaf886fd5ebc37f8ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205835"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Zaimplementuj standardowe konstruktory wyjątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Rozszerza typ <xref:System.Exception?displayProperty=fullName> i nie deklaruje wymagane konstruktorów.

## <a name="rule-description"></a>Opis reguły
 Typy wyjątków należy zaimplementować następujących konstruktorów:

- NewException() publiczne

- NewException(string) publiczne

- publiczne NewException (ciąg, wyjątku)

- NewException chroniona lub prywatnej (SerializationInfo, StreamingContext)

  Niepowodzenie podczas dostarczenia pełnego zestawu konstruktorów może utrudnić poprawną obsługę wyjątków. Na przykład konstruktora, który ma podpis `NewException(string, Exception)` służy do tworzenia wyjątków, które są spowodowane przez inne wyjątki. Bez tego konstruktora nie może utworzyć i zgłosić wystąpienie usługi niestandardowy wyjątek, który zawiera wewnętrzny wyjątek (zagnieżdżona) czyli jakich kodu zarządzanego, należy wykonać w takiej sytuacji. Pierwsze konstruktory wyjątku trzech są publiczne przez Konwencję. Czwarty Konstruktor jest chronione niezapieczętowanych klas i prywatny w klasach zapieczętowanych. Aby uzyskać więcej informacji, zobacz [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Dodaj brakujące konstruktory wyjątek i upewnij się, że poprawne ułatwień dostępu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli naruszenie jest spowodowany przez przy użyciu poziomu różny dostęp dla konstruktorów publicznych.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera typ wyjątku, który narusza tę regułę i typ wyjątku, który jest implementowana prawidłowo.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
