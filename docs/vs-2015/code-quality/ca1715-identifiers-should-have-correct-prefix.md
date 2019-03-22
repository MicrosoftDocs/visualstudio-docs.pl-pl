---
title: 'CA1715: Identyfikatory powinny mieć poprawny prefiks | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cece70c942b62390e0ba3e96c57c1c46c4dd46fa
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355152"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Identyfikatory powinny mieć poprawny prefiks
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1715: Identyfikatory powinny mieć poprawny prefiks](https://docs.microsoft.com/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) w witrynie docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Przerywanie — gdy wywoływane na interfejsach.<br /><br /> Bez podziału — gdy wywoływane w parametrach typu ogólnego.|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa widocznego na zewnątrz interfejsu nie rozpoczyna się od wielkie litery "I".  
  
 —lub—  
  
 Nazwa parametru typu ogólnego na widocznych zewnętrznie typie lub metodzie nie rozpoczyna się od wielkiej litery t ".  
  
## <a name="rule-description"></a>Opis reguły  
 Według Konwencji nazwy niektórych elementów programowania zaczynać od określonego prefiksu.  
  
 Nazwy interfejsów powinna rozpoczynać się wielką który "I" następuje innego wielką literą. Ta zasada zgłasza naruszenia nazwy interfejsu, takie jak "MyInterface" i "IsolatedInterface".  
  
 Nazwy parametrów typu ogólnego powinien zaczynać się wielką t "i opcjonalnie może następować innego wielką literą. Ta zasada zgłasza naruszenia nazwy parametru typu ogólnego, takie jak "V" i "Type".  
  
 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmień nazwę identyfikatora, tak, aby poprawnie jest poprzedzana.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 **Poniższy kod przedstawia interfejs niepoprawnie nazwanych.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.vb#1)]  
  
## <a name="example"></a>Przykład  
 **Poniższy przykład naprawia wcześniejszego naruszenia praw przez dodanie przedrostka interfejsu prefiksem "I".**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.vb#1)]  
  
## <a name="example"></a>Przykład  
 **Poniższy przykład pokazuje parametr niepoprawnie o nazwie typu ogólnego.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.vb#1)]  
  
## <a name="example"></a>Przykład  
 **Poniższy przykład naprawia wcześniejszego naruszenia praw przez dodanie przedrostka parametr typu ogólnego przy użyciu t ".**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1722: Identyfikatory nie powinny mieć niepoprawnego prefiksu](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)
