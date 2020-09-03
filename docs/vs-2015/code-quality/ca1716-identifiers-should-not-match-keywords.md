---
title: 'CA1716: identyfikatory nie powinny być zgodne ze słowami kluczowymi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 67a3588a857a0eea7d338217f975ed593dfdad52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543705"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Identyfikatory nie powinny być zgodne ze słowami kluczowymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa przestrzeni nazw, typu lub viritual lub składowej interfejsu pasuje do zastrzeżonego słowa kluczowego w języku programowania.

## <a name="rule-description"></a>Opis reguły
 Identyfikatory przestrzeni nazw, typów i elementów członkowskich wirtualnych i interfejsów nie powinny być zgodne ze słowami kluczowymi, które są zdefiniowane przez Języki przeznaczone dla środowiska uruchomieniowego języka wspólnego. W zależności od używanego języka i słowa kluczowego, błędy kompilatora i niejasności mogą utrudniać korzystanie z biblioteki.

 Ta reguła sprawdza słowa kluczowe w następujących językach:

- Visual Basic

- C#

- C++/CLI

  Porównanie bez uwzględniania wielkości liter jest używane dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] słów kluczowych, a porównanie uwzględniające wielkość liter jest używane dla innych języków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wybierz nazwę, która nie jest wyświetlana na liście słów kluczowych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Możesz pominąć ostrzeżenie z tej reguły, Jeśli wiesz, że identyfikator nie będzie mylić użytkowników interfejsu API i że biblioteka jest użyteczna we wszystkich dostępnych językach w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .
