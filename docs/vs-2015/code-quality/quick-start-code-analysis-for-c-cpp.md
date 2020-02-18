---
title: 'Szybki start: Analiza kodu C-C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e9db06ec0748ce4499afb423fac03886cd763301
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278481"
---
# <a name="quick-start-code-analysis-for-cc"></a>Szybki start: Analiza kodu dla C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jakość aplikacji można poprawić, uruchamiając analizę kodu regularnie w języku C lub C++ kodzie. Może to pomóc w znalezieniu typowych problemów, naruszeniu dobrych rozwiązań programistycznych lub wad, które trudno wykryć poprzez testowanie. Ostrzeżenia analizy kodu różnią się od błędów i ostrzeżeń, ponieważ analiza kodu szuka wzorców konkretnego kodu, które są prawidłowe, ale nadal można tworzyć problemy dla Ciebie lub innych osób używających Twojego kodu.  
  
## <a name="in-this-topic"></a>W tym temacie  
  
- [Konfigurowanie zestawów reguł dla projektu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [Uruchom analizę kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [Analizowanie i rozwiązywanie ostrzeżeń dotyczących analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [Pomijanie ostrzeżeń analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [Tworzenie elementów roboczych dla ostrzeżeń analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [Wyszukiwanie i filtrowanie wyników analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="BKMK_ConfigureRuleSets"></a>Konfigurowanie zestawów reguł dla projektu  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla nazwy projektu, a następnie wybierz polecenie **Właściwości**.  
  
2. Następujące kroki są opcjonalne:  
  
    1. Na listach **Konfiguracja** i **platforma** wybierz konfigurację kompilacji i platformę docelową.  
  
    2. Domyślnie program analizy kodu nie raportuje ostrzeżenia z kodu, który jest generowany automatycznie przez narzędzia zewnętrzne. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, wyczyść pole wyboru **Pomiń wyniki z wygenerowanego kodu** .  
  
        > [!NOTE]
        > Ta opcja nie pomija błędy analizy kodu i ostrzeżenia z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Można zarówno wyświetlać, jak i konserwować kod źródłowy formularza lub szablonu.  
  
3. Aby uruchomić analizę kodu za każdym razem, gdy projekt jest kompilowany przy użyciu wybranej konfiguracji, zaznacz pole wyboru **Włącz analizę koduC++ dla C/on Build** . Możesz również ręcznie uruchomić analizę kodu, otwierając menu **Analizuj** , a następnie wybierając polecenie **Uruchom analizę kodu na** *ProjectName*.  
  
4. Na liście **Uruchom ten zestaw reguł** wykonaj jedną z następujących czynności:  
  
    - Wybierz zestaw reguł, którego chcesz użyć.  
  
    - Wybierz **\<Przeglądaj... >** określić istniejącego niestandardowego zestawu reguł, którego nie ma na liście.  
  
    - Zdefiniuj niestandardowy zestaw reguł.  
  
         Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Standardowe C/C++ zestawy reguł  
 Program Visual Studio zawiera dwa standardowe zestawy reguł dla kodu natywnego:  
  
|Zestaw reguł|Opis|  
|--------------|-----------------|  
|Minimalne zalecane reguły natywne firmy Microsoft|Ten zestaw reguł dotyczy najważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Ten zestaw reguł powinien być dołączany do każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|  
|Zalecane reguły natywne firmy Microsoft|Ten zestaw reguł obejmuje szeroki zakres problemów. Zawiera wszystkie reguły w minimalnych zalecanych regułach firmy Microsoft w języku macierzystym.|  
  
## <a name="BKMK_Run"></a>Uruchom analizę kodu  
 Na stronie Analiza kodu na stronach właściwości projektu można skonfigurować analizę kodu, która będzie uruchamiana za każdym razem, gdy kompilujesz projekt. Możesz również ręcznie uruchomić analizę kodu.  
  
 Aby uruchomić analizę kodu w rozwiązaniu:  
  
- W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu w rozwiązaniu**.  
  
  Aby uruchomić analizę kodu w projekcie:  
  
- W Eksplorator rozwiązań wybierz nazwę projektu.  
  
- W menu **kompilacja** wybierz polecenie **Uruchom analizę kodu dla** *nazwy projektu*.  
  
  Projekt lub rozwiązanie zostały skompilowane i zostanie uruchomiona Analiza kodu. Wyniki są wyświetlane w oknie analizy kodu.  
  
## <a name="BKMK_Analyze"></a>Analizowanie i rozwiązywanie ostrzeżeń dotyczących analizy kodu  
 Aby analizować szczególne ostrzeżenie, wybierz tytuł ostrzeżenia w oknie analizy kodu. Ostrzeżenie zostanie rozwinięte, aby wyświetlić dodatkowe informacje o problemie. Gdy jest to możliwe, analiza kodu wyświetla numery wierszy i logikę analizy, które doprowadziły do ostrzeżenia. Aby uzyskać szczegółowe informacje o ostrzeżeniu, w tym o możliwych rozwiązaniach problemu, wybierz identyfikator ostrzeżenia, aby wyświetlić temat pomocy w bibliotece MSND dla wiadomości.  
  
 Po rozwinięciu ostrzeżenie w wierszu kodu, który spowodował ostrzeżenie jest wyróżniony w edytorze kodu programu Visual Studio.  
  
 Po zrozumieniu problem można rozwiązać, w kodzie. Następnie uruchom ponownie analizę kodu, aby upewnić się, że ostrzeżenie nie jest już wyświetlany w oknie analizy kodu i rozwiązanie problemu nie został zgłoszony nowe ostrzeżenia.  
  
> [!TIP]
> Możesz ponownie uruchomić analizę kodu w oknie analizy kodu. Wybierz przycisk **Analizuj** i wybierz zakres analizy. Możesz ponownie uruchomić analizy na całego rozwiązania lub wybranego projektu.  
  
## <a name="BKMK_Suppress"></a>Pomijanie ostrzeżeń analizy kodu  
 Istnieją terminy, gdy można zdecydować, Rezygnacja z naprawiania ostrzeżenie analizy kodu. Można zdecydować, rozpoznawanie ostrzeżenia wymaga zbyt dużo nagrywanie względem prawdopodobieństwo wystąpienia problemu w implementacji rzeczywistych swój kod. Lub może być uważa, że analizy, który jest używany w ostrzeżenia jest nieodpowiedni dla określonego kontekstu. Poszczególne ostrzeżenia można pominąć, tak aby nie były widoczne w oknie analizy kodu.  
  
 Aby pominąć Ostrzeżenie:  
  
1. Jeśli szczegółowe informacje nie są wyświetlane, wybierz tytuł ostrzeżenia, aby go rozwinąć.  
  
2. Wybierz łącze **Akcje** u dołu ostrzeżenia.  
  
3. Wybierz pozycję **Pomiń komunikat** , a następnie wybierz pozycję **w polu Źródło**.  
  
   Pomijanie komunikatu powoduje wstawienie `#pragma warning (disable:`*WarningId*`)`, które pomija Ostrzeżenie dla wiersza kodu.  
  
## <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a>Tworzenie elementów roboczych dla ostrzeżeń analizy kodu  
 Za pomocą funkcji śledzenia elementów roboczych można rejestrować usterki w programie Visual Studio. Aby użyć tej funkcji, należy nawiązać połączenie z wystąpieniem Team Foundation Server.  
  
 **Aby utworzyć element roboczy dla co najmniej jednego ostrzeżenia C/C++ Code**  
  
1. W oknie Analiza kodu rozwiń i wybierz ostrzeżenia  
  
2. W menu skrótów dla ostrzeżeń wybierz polecenie **Utwórz element roboczy**, a następnie wybierz typ elementu pracy.  
  
3. Program Visual Studio tworzy pojedynczy element roboczy dla wybranych ostrzeżeń i wyświetla element roboczy w oknie dokumentu IDE.  
  
4. Dodaj wszelkie dodatkowe informacje, a następnie wybierz pozycję **Zapisz element roboczy**.  
  
## <a name="BKMK_Search"></a>Wyszukiwanie i filtrowanie wyników analizy kodu  
 Możesz wyszukiwać długim spisem komunikaty ostrzegawcze i filtrować ostrzeżeń w rozwiązaniach dotyczących wielu projektów.  
  
1. **Aby filtrować ostrzeżenia według tytułu lub identyfikatora ostrzeżenia**: Wprowadź słowo kluczowe w polu tekstowym **Filtr** .  
  
2. **Aby odfiltrować ostrzeżenia według projektu**: w rozwiązaniu z wieloma projektami wybierz jeden lub więcej projektów z listy w prawym górnym rogu okna Analiza kodu. Wybierz nazwę rozwiązania, aby wyświetlić wszystkie ostrzeżenia.  
  
3. **Aby filtrować ostrzeżenia według ważności**: domyślnie komunikaty analizy kodu są przypisywane ważności **ostrzeżenia**. Można przypisać ważność co najmniej jednego komunikatu jako **błąd** w niestandardowym zestawie reguł. Wybierz opcję **Ostrzeżenie** lub **błąd** , aby wyświetlić tylko te komunikaty, do których przypisano odpowiednią ważność. Wybierz opcję **wszystkie** , aby wyświetlić wszystkie komunikaty.
