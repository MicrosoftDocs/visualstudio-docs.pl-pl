---
title: 'Szybki start: Analiza kodu C i c++ | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 83b793f694c1965f5ded6b0fd136d672280d59cc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54789866"
---
# <a name="quick-start-code-analysis-for-cc"></a>Szybki start: Analiza kodu C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby poprawić jakość aplikacji, należy regularnie uruchamiania analizy kodu dla kodu C lub C++. To może pomóc w znalezieniu typowe problemy, naruszeń dobrą praktyką programowania lub usterki, które są trudne do odnajdywania za pomocą testowania. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń, ponieważ analiza kodu szuka wzorców konkretnego kodu, które są prawidłowe, ale nadal można tworzyć problemy dla Ciebie lub innych osób używających Twojego kodu.  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Konfigurowanie zestawów reguł dla projektu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
-   [Przeprowadź analizę kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
-   [Analizowanie i rozwiązywanie ostrzeżenia analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
-   [Pomijanie ostrzeżeń analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
-   [Tworzenie elementów roboczych dla kodu ostrzeżenia analizy](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
-   [Wyszukiwanie i filtrowanie wyników analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
##  <a name="BKMK_ConfigureRuleSets"></a> Konfigurowanie zestawów reguł dla projektu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla nazwy projektu, a następnie wybierz **właściwości**.  
  
2.  Poniższe kroki są opcjonalne:  
  
    1.  W **konfiguracji** i **platformy** listy, wybierz platformę kompilacji konfiguracji i docelowej.  
  
    2.  Domyślnie program analizy kodu nie raportuje ostrzeżenia z kodu, który jest generowany automatycznie przez narzędzia zewnętrzne. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, należy wyczyścić **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.  
  
        > [!NOTE]
        >  Ta opcja nie pomija błędy analizy kodu i ostrzeżenia z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Można wyświetlać lub zachować kod źródłowy dla formularza lub szablonu.  
  
3.  Aby uruchomić analizę kodu, za każdym razem, gdy projekt jest kompilowany przy użyciu wybranej konfiguracji, zaznacz **Włącz analizę kodu C/c++ podczas kompilacji** pole wyboru. Można również uruchomić analizę kodu ręcznie, otwierając **analizy** menu, a następnie wybierając **Uruchom analizę kodu dla** *ProjectName*.  
  
4.  W **Uruchom ten zestaw reguł** listy, wykonaj jedną z następujących czynności:  
  
    -   Wybierz zestaw reguł, który chcesz użyć.  
  
    -   Wybierz  **\<Przeglądaj … >** do określenia, ustaw istniejącej reguły niestandardowe, który nie jest na liście.  
  
    -   Definiowanie niestandardowego zestawu reguł.  
  
         Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Standard języka C/C++ zestawy reguł  
 Program Visual Studio zawiera dwa standardowe zestawy reguł dla kodu natywnego:  
  
|Zestaw reguł|Opis|  
|--------------|-----------------|  
|Zalecane reguły kodu natywnego firmy Microsoft, co najmniej|Ten zestaw reguł koncentruje się na najważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|  
|Zalecane reguły kodu natywnego firmy Microsoft|Ten zestaw reguł obejmuje szerokiej gamy problemów. Zawiera ono wszystkie reguły w Microsoft Native Minimum reguł zalecanych.|  
  
##  <a name="BKMK_Run"></a> Przeprowadź analizę kodu  
 Na stronie analizy kodu na stronach właściwości projektu można skonfigurować analizy kodu do uruchomienia każdorazowo kompilacji projektu. Można również uruchamiać analizę kodu ręcznie.  
  
 Aby uruchomić analizę kodu na rozwiązanie:  
  
- Na **kompilacji** menu, wybierz **Uruchom analizę kodu dla rozwiązania**.  
  
  Aby uruchomić analizę kodu w projekcie:  
  
- W Eksploratorze rozwiązań wybierz nazwę projektu.  
  
- Na **kompilacji** menu, wybierz **Uruchom analizę kodu dla** *Nazwa projektu*.  
  
  Projektu lub rozwiązania jest kompilowana i uruchamia analizy kodu. Wyniki są wyświetlane w oknie analizy kodu.  
  
##  <a name="BKMK_Analyze"></a> Analizowanie i rozwiązywanie ostrzeżenia analizy kodu  
 Aby analizować szczególne ostrzeżenie, wybierz tytuł ostrzeżenia w oknie analizy kodu. Ostrzeżenie rozwija, aby wyświetlić dodatkowe informacje o problemie. Jeśli to możliwe, analizy kodu wyświetla numery wierszy i logika analizy, które doprowadziło do ostrzeżenia. Aby uzyskać szczegółowe informacje na temat ostrzeżenia, w tym możliwe rozwiązania problemu należy wybrać identyfikator ostrzeżenia, aby wyświetlić tematu pomocy w bibliotece MSND dla wiadomości.  
  
 Po rozwinięciu ostrzeżenie w wierszu kodu, który spowodował ostrzeżenie jest wyróżniony w edytorze kodu programu Visual Studio.  
  
 Po zrozumieniu problem można rozwiązać, w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenie nie jest już wyświetlany w oknie analizy kodu i rozwiązanie problemu nie został zgłoszony nowe ostrzeżenia.  
  
> [!TIP]
>  Możesz ponownie uruchomić analizę kodu w oknie analizy kodu. Wybierz **analizy** przycisk, a następnie wybierz zakres analizy. Możesz ponownie uruchomić analizy na całego rozwiązania lub wybranego projektu.  
  
##  <a name="BKMK_Suppress"></a> Pomijanie ostrzeżeń analizy kodu  
 Istnieją terminy, gdy można zdecydować, Rezygnacja z naprawiania ostrzeżenie analizy kodu. Można zdecydować, rozpoznawanie ostrzeżenia wymaga zbyt dużo nagrywanie względem prawdopodobieństwo wystąpienia problemu w implementacji rzeczywistych swój kod. Lub może być uważa, że analizy, który jest używany w ostrzeżenia jest nieodpowiedni dla określonego kontekstu. Poszczególne ostrzeżenia można pominąć, tak aby nie były widoczne w oknie analizy kodu.  
  
 Aby pominąć Ostrzeżenie:  
  
1. Jeśli nie są wyświetlane szczegółowe informacje, wybierz tytuł ostrzeżenie, aby ją rozwinąć.  
  
2. Wybierz **akcje** widocznego u dołu ostrzeżenia.  
  
3. Wybierz **Pomiń komunikat** , a następnie wybierz **w źródłowej**.  
  
   Pomijanie wiadomości wstawia `#pragma warning (disable:` *WarningId* `)` który umożliwia pominięcie ostrzeżenia dla wiersza kodu.  
  
##  <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Tworzenie elementów roboczych dla kodu ostrzeżenia analizy  
 Element roboczy, funkcja śledzenia umożliwia rejestrowanie błędów z poziomu programu Visual Studio. Aby użyć tej funkcji, należy połączyć się z wystąpieniem programu Team Foundation Server.  
  
 **Aby utworzyć element roboczy dla co najmniej jedno ostrzeżenie kodu C/C++**  
  
1.  W oknie analizy kodu Rozwiń i wybierz ostrzeżenia  
  
2.  W menu skrótów dla ostrzeżenia wybierz **Utwórz element pracy**, a następnie wybierz typ elementu roboczego.  
  
3.  Program Visual Studio tworzy pojedynczym elemencie roboczym dla wybranych ostrzeżeń i wyświetla element roboczy w oknie dokumentu w IDE.  
  
4.  Dodaj wszelkie dodatkowe informacje, a następnie wybierz **Zapisz element roboczy**.  
  
##  <a name="BKMK_Search"></a> Wyszukiwanie i filtrowanie wyników analizy kodu  
 Możesz wyszukiwać długim spisem komunikaty ostrzegawcze i filtrować ostrzeżeń w rozwiązaniach dotyczących wielu projektów.  
  
1.  **Aby ostrzeżeń filtru według tytułu lub identyfikator ostrzeżenia**: Wprowadź słowa kluczowego w **filtru** pola tekstowego.  
  
2.  **Aby ostrzeżeń filtru przez projekt**: W ramach rozwiązania wielu projektów, wybierz jeden lub więcej projektów, na liście u góry po prawej krawędzi okna analizy kodu. Wybierz nazwę rozwiązania, aby wyświetlić wszystkie ostrzeżenia.  
  
3.  **Aby ostrzeżeń filtru według ważności**: Domyślnie komunikaty analizy kodu są przypisywane ważność **ostrzeżenie**. Możesz przypisać wagi co najmniej jedna wiadomość jako **błąd** w zestawie reguł niestandardowych. Wybierz opcję **ostrzeżenie** lub **błąd** do wyświetlenia tylko komunikaty, które są przypisane do odpowiednich ważności. Wybierz **wszystkich** można wyświetlić wszystkie komunikaty.
