---
title: W obszarze Przegląd pomijanie źródła | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 046ae576880c6749c6bb033f66124c0085dfab16
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057163"
---
# <a name="in-source-suppression-overview"></a>Ograniczanie w kodzie źródłowym - Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomijanie w źródła jest możliwość pominąć lub zignorować naruszeń analizy kodu w kodzie zarządzanym przez dodanie **SuppressMessage** atrybutu segmenty kodu, które powodują naruszenia. **SuppressMessage** atrybutu jest atrybut conditional, który jest dostępny w metadanych IL zestawu kodu zarządzanego, tylko wtedy, gdy zdefiniowano symbol kompilacji CODE_ANALYSIS w czasie kompilacji.  
  
 W C++sposób niezamierzony, użyj makra CA_SUPPRESS_MESSAGE lub CA_GLOBAL_SUPPRESS_MESSAGE w pliku nagłówkowym dodać atrybut.  
  
 Nie należy używać w źródłowej pominięcia kompilacji do wydania aby zapobiec przypadkowo wysyłania metadanych pomijanie w źródła. Ze względu na koszt przetwarzania pomijanie-source wydajność aplikacji może być znacznie umieszczając metadanych pomijanie w źródła.  
  
> [!NOTE]
>  Nie masz ręcznie kod te atrybuty samodzielnie. Aby uzyskać więcej informacji, zobacz [jak: Pomijanie ostrzeżeń przy użyciu elementu Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Element menu nie jest dostępne dla kodu C++.  
  
## <a name="suppressmessage-attribute"></a>Atrybutu SuppressMessage  
 Po kliknięciu prawym przyciskiem myszy ostrzeżenia analizy kodu w **lista błędów** a następnie kliknij przycisk **Pomijaj komunikaty**, **SuppressMessage** jest dodawany atrybut, w kodzie lub do Plik pominięć globalnych projektu.  
  
 **SuppressMessage** atrybut ma następujący format:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Gdzie:  
  
- **Reguła kategorii** -kategorii, w którym zdefiniowano reguły. Aby uzyskać więcej informacji na temat kategorie reguł analizy kodu, zobacz [analiza kodu dla zarządzanego kodu ostrzeżenia](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
- **Identyfikator reguły** — identyfikator reguły. Obsługa obejmuje zarówno krótko- i nazwę dla identyfikatora reguły. Krótka nazwa jest CAXXXX; długa nazwa jest CAXXXX:FriendlyTypeName.  
  
- **Uzasadnienie** — tekst, który umożliwia dokumentowanie przyczyny pomijanie komunikatu.  
  
- **Identyfikator komunikatu** — Unikatowy identyfikator problemu dla każdego komunikatu.  
  
- **Zakres** — element docelowy, na którym pomijane jest ostrzeżenie. Jeśli element docelowy nie zostanie określony, ustawiono element docelowy atrybutu. Zakresy obsługiwane są następujące:  
  
    - Moduł  
  
    - Przestrzeń nazw  
  
    - Zasób  
  
    - Typ  
  
    - Element członkowski  
  
- **Docelowy** — identyfikator, który służy do określania docelowych, na którym pomijane jest ostrzeżenie. Musi zawierać element w pełni kwalifikowaną nazwę.  
  
## <a name="suppressmessage-usage"></a>Użycie SuppressMessage  
 Ostrzeżenia analizy kodu są pomijane w poziomie, do którego wystąpienia **SuppressMessage** atrybut jest stosowany. Celem tego jest ściśle Połącz informacji pomijanie w kodzie realizowana naruszenia.  
  
 Ogólna postać pomijania zawiera kategoria reguł i identyfikator reguły, który zawiera opcjonalne czytelny dla człowieka reprezentację nazwę reguły. Na przykład  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 W przypadku ze względu na wydajność strict do minimalizowania pomijanie w źródła metadanych sama nazwa reguły może pozostać w. Kategoria reguły wraz z jego identyfikator reguły stanowić wystarczająco Unikatowy identyfikator reguły. Na przykład  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Ten format nie jest zalecane z powodu problemów łatwości utrzymania.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Pomijanie wielu naruszeń w treści metody  
 Atrybuty można stosować tylko do metody i nie mogą być osadzone w treści metody. Można jednak określić identyfikator, jako identyfikator komunikatu w celu rozróżnienia wielu wystąpień naruszenie wewnątrz metody.  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>Wygenerowany kod  
 Kompilatory kodu zarządzanego i niektóre narzędzia innych firm generowanie kodu w celu ułatwienia tworzenia szybkie kodu. Kod wygenerowany przez kompilator, który pojawia się w plikach źródłowych jest zwykle oznaczony przy użyciu **GeneratedCodeAttribute** atrybutu.  
  
 Możesz wybrać, czy pominąć ostrzeżenia analizy kodu i błędów dla wygenerowanego kodu. Aby uzyskać informacje o tym, jak pominąć tych ostrzeżeń i błędów, zobacz [jak: Pomijanie ostrzeżeń dla wygenerowanego kodu](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Należy zauważyć, że analiza kodu ignoruje **GeneratedCodeAttribute** gdy jest stosowany do całego zestawu lub jeden parametr. Tych sytuacji występują rzadko.  
  
## <a name="global-level-suppressions"></a>Pominięcia na poziomie globalnym  
 Narzędzie do analizy kodu zarządzanego analizuje **SuppressMessage** atrybutów, które są stosowane na poziomie zestawu, modułu, typu, składowej lub parametr. Jest również uruchamiana naruszeń względem zasobów i przestrzeni nazw. Te naruszenia musi zostać zastosowana na poziomie globalnym i są zakres i docelowe. Na przykład następujący komunikat pomija naruszenie przestrzeni nazw:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Ostrzeżenie o zakresie przestrzeni nazw zostanie pominięty, powoduje pominięcie ostrzeżenie przed samej przestrzeni nazw. Ostrzeżenie typów w przestrzeni nazw, nie są odrzuca.  
  
 Wszelkie pomijanie może być wyrażona przez określenie zakresu jawnego. Pominięcia na te muszą znajdować się na poziomie globalnym. Nie można określić poziom elementu członkowskiego pomijanie przez urządzanie typu.  
  
 Pominięcia na poziomie globalne są jedynym sposobem na wyświetlanie komunikatów, które odwołują się do kodu generowanego przez kompilator, który nie jest mapowany na źródło jawnie podaną użytkownika. Na przykład poniższy kod powoduje pominięcie naruszenie przed konstruktorem emitowane przez kompilator:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Docelowy zawsze zawiera nazwę elementu w pełni kwalifikowana.  
  
## <a name="global-suppression-file"></a>Plik globalne pomijanie  
 Plik pominięć globalnych zachowuje ograniczeń, które są pominięcia na poziomie globalnym lub pominięcia, których nie określono elementu docelowego. Na przykład ograniczeń dla zestawu poziomu naruszeń są przechowywane w tym pliku. Ponadto niektórych ograniczeń ASP.NET są przechowywane w tego pliku, ponieważ ustawienia na poziomie projektu nie są dostępne dla kod związany z formularzem. Globalne pomijanie jest tworzone i dodawane do projektu po raz pierwszy wybierzesz **w pliku pominięć projektu** opcji **Pomijaj komunikaty** polecenia w oknie Lista błędów. Aby uzyskać więcej informacji, zobacz [jak: Pomijanie ostrzeżeń przy użyciu elementu Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.CodeAnalysis>
