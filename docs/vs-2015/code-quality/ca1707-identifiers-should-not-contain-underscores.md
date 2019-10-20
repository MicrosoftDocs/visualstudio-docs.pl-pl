---
title: 'CA1707: identyfikatory nie powinny zawierać podkreśleń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 526f0333cc4a233996c00576e3439bac4593c29f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669213"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Identyfikatory nie powinny zawierać podkreśleń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1707: identyfikatory nie powinny zawierać podkreśleń](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Przerywanie — gdy są wywoływane w zestawach<br /><br /> Rozdzielenie — gdy zostanie wywołane w parametrach typu|

## <a name="cause"></a>Przyczyna
 Nazwa identyfikatora zawiera znak podkreślenia (_).

## <a name="rule-description"></a>Opis reguły
 Przez konwencję identyfikatory nazw nie zawierają znaku podkreślenia (_). Reguła sprawdza przestrzenie nazw, typy, elementy członkowskie i parametry.

 Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Usuń wszystkie znaki podkreślenia z nazwy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
