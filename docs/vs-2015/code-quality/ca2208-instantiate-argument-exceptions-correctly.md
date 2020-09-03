---
title: 'CA2208: Utwórz poprawnie wystąpienia wyjątków argumentów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a63ebb7f3946926864c4dd882c281b5dcd7c6c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535840"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Poprawnie twórz wystąpienia wyjątków argumentów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Możliwe przyczyny są następujące:

- Wykonano wywołanie domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest lub pochodzi z [System. ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

- Niepoprawny argument ciągu jest przenoszona do sparametryzowanego konstruktora typu wyjątku, który jest lub pochodzi z [System. ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Opis reguły
 Zamiast wywoływania domyślnego konstruktora, wywołaj jedno z przeciążeń konstruktora, które pozwala na podano bardziej zrozumiały komunikat wyjątku. Komunikat o wyjątku powinien wskazywać dewelopera i jasno wyjaśnić warunek błędu oraz jak poprawić lub uniknąć wyjątku.

 Sygnatury jednego i dwóch konstruktorów ciągów <xref:System.ArgumentException> i jego typów pochodnych nie są spójne z uwzględnieniem `message` `paramName` parametrów i. Upewnij się, że te konstruktory są wywoływane z prawidłowymi argumentami ciągu. Podpisy są następujące:

 <xref:System.ArgumentException>(ciąg `message` )

 <xref:System.ArgumentException>(String `message` , String `paramName` )

 <xref:System.ArgumentNullException>(ciąg `paramName` )

 <xref:System.ArgumentNullException>(String `paramName` , String `message` )

 <xref:System.ArgumentOutOfRangeException>(ciąg `paramName` )

 <xref:System.ArgumentOutOfRangeException>(String `paramName` , String `message` )

 <xref:System.DuplicateWaitObjectException>(ciąg `parameterName` )

 <xref:System.DuplicateWaitObjectException>(String `parameterName` , String `message` )

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Wywołaj konstruktora, który przyjmuje komunikat, nazwę parametru lub oba parametry, i upewnij się, że argumenty są odpowiednie dla typu <xref:System.ArgumentException> wywoływanego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły tylko wtedy, gdy Konstruktor sparametryzowany jest wywoływany z prawidłowymi argumentami ciągu.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje Konstruktor, który nieprawidłowo tworzy wystąpienie typu ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia powyższe naruszenie, przełączając argumenty konstruktora.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
