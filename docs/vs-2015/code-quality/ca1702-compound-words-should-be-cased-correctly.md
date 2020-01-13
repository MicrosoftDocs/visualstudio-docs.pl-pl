---
title: 'CA1702: wyrazy złożone powinny mieć prawidłową wielkość liter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 854e9a492f422957e64e1a4b6a00bc7c39b81c46
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919241"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Wyrazy złożone należy zapisywać z uwzględnieniem wielkości liter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1702: wyrazy złożone powinny mieć poprawną wielkość liter](/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly).

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Przerywanie — gdy są uruchamiane w zestawach.<br /><br /> Rozdzielenie — gdy jest uruchamiany w parametrach typu.|

## <a name="cause"></a>Przyczyna
 Nazwa identyfikatora zawiera wiele wyrazów, a co najmniej jeden wyraz wydaje się wyrazem złożonym, który nie jest poprawna.

## <a name="rule-description"></a>Opis reguły
 Nazwa identyfikatora jest dzielona na wyrazy, które są oparte na wielkości liter. Każda ciągła kombinacja dwóch wyrazów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeśli zostanie rozpoznany, identyfikator powoduje naruszenie reguły. Przykładami wyrazów złożonych, które powodują naruszenie, są "CheckSum" i "wieloczęściowa", które powinny być odpowiednio określone jako "Checksum" i "wieloczęściowa". Ze względu na poprzednie typowe użycie, kilka wyjątków jest wbudowanych w regułę, a kilka pojedynczych wyrazów jest oflagowanych, takich jak "Toolbar" i "filename", które powinny być rozróżniane jako dwa oddzielne słowa (w tym przypadku "ToolBar" i "FileName").

 Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień nazwę tak, aby była uwzględniana wielkość liter.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli obie części wyrazu złożonego są rozpoznawane przez słownik pisowni, można bezpiecznie pominąć ostrzeżenie z tej reguły, a zamiarem jest użycie dwóch wyrazów.

## <a name="related-rules"></a>Powiązane reguły
 [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Zobacz też
 [Zasady nazewnictwa](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) — [konwencje wielką literą](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
