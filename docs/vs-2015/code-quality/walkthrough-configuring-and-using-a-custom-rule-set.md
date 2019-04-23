---
title: 'Przewodnik: Konfigurowanie i używanie niestandardowego zestawu reguł | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: da7b1f1bda7fac222d0d47c6bf2a15eaf3a8396f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052067"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Przewodnik: Konfigurowanie niestandardowego zestawu reguł i korzystanie z niego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten poradnik pokazuje jak używać narzędzi analizy kodu, które zostały skonfigurowane do użycia dostosowany *zestaw reguł* w bibliotece klas. Możesz wybrać zestaw reguł, który odnosi się do typu projektu, który został określony dla rozwiązania, lub wybrać alternatywne reguły zestawy, aby spełnić szczególną potrzebę, takie jak skanowanie ze starszym kodem dla problemów, które można naprawić w sposób nieprzerywającymi działania aplikacji. W obu przypadkach można także dostosowywać w celu dostosowania ich do wymagań projektu zestawów reguł.  
  
 W tym przewodniku przechodzi przez te procesy:  
  
- Utwórz bibliotekę klas.  
  
- Wybierz **podstawowe reguły wskazówek dotyczących projektowania firmy Microsoft** zestawu reguł analizy kodu.  
  
- Dodaj własny kod do klasy.  
  
- Przeprowadź analizę kodu.  
  
- Dostosuj zestaw reguł.  
  
- Uruchom analizę kodu i zobacz, jak reguły ustawić dostosowywania zachowania działa.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], lub [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="using-rule-sets-with-code-analysis"></a>Korzystanie z zestawów reguł analizy kodu  
 Najpierw Utwórz bibliotekę klas proste.  
  
#### <a name="create-a-class-library"></a>Utwórz bibliotekę klas  
  
1. Na **pliku** menu, kliknij przycisk **New** a następnie kliknij przycisk **projektu**.  
  
2. W **nowy projekt** dialogowego **typów projektów**, kliknij przycisk **Visual C#**.  
  
3. W obszarze **Visual C#**, wybierz opcję **biblioteki klas**.  
  
4. W **nazwa** polu tekstowym **RuleSetSample** a następnie kliknij przycisk **OK**.  
  
   Następnie należy wybrać **podstawowe reguły wskazówek dotyczących projektowania firmy Microsoft** zestaw reguł i zapisz go z projektu.  
  
#### <a name="select-a-code-analysis-rule-set"></a>Wybierz zestaw reguł analizy kodu  
  
1. Na **analizy** menu, kliknij przycisk **Konfigurowanie analizy kodu dla RuleSetSample**.  
  
    Ustawienia konfiguracji dla analizy kodu będą wyświetlane.  
  
2. W **Uruchom ten zestaw reguł** listy rozwijanej wybierz **wszystkie reguły firmy Microsoft**.  
  
    Aby uzyskać więcej informacji na temat zestawów dostępności reguł, zobacz [odwołanie zestawu reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md).  
  
    W menu Plik kliknij polecenie **Zapisz wybrane elementy** można zaktualizować pliku projektu przy użyciu informacji o zestawie reguł, które wybrano i jego ustawień.  
  
   > [!TIP]
   >  W rzeczywistych sytuacji, dobrą praktyką jest nadawanie priorytetów problemy, które chcesz przeanalizować za pomocą analizy kodu na użytek jest rozpoczęcie od **Minimum Rules zalecane** zestaw reguł i rozwiązać problemy żądaną i stopniowo dodawać więcej reguł lub reguła ustawia znaleźć i poprawić dodatkowe problemy.  
  
   Następnie dodasz kod do biblioteki klas, które będzie używane w celu wykazania naruszeń CA1704 "Identyfikatory powinny być zapisane poprawnie" reguł analizy kodu. Aby uzyskać więcej informacji, zobacz [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### <a name="add-your-own-code"></a>Dodaj własny kod  
  
- W Eksploratorze rozwiązań Otwórz plik Class1.cs i Zastąp istniejący kod następujących czynności:  
  
  ```  
  using System;  
  using System.Collections.Generic;  
  using System.Text;  
  
  namespace RuleSetSample  
  {  
      public class Class1  
      {  
          //The variable parameter names "a" and "b" will cause  
          //the warning CA 1704 Microsoft.Naming "Consider   
          //providing a more meaningful name" to fire  
          public int AddIntegers(int a, int b)  
          {  
  
              int sum = a + b;  
  
              return (sum);  
          }  
      }  
  }  
  
  ```  
  
  Teraz można uruchomić analizę kodu w projekcie RuleSetSample i odszukaj wszelkie błędy i ostrzeżenia wygenerowane w oknie Lista błędów.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Przeprowadź analizę kodu w projekcie RuleSetSample  
  
1. Na **analizy** menu, kliknij przycisk **Uruchom analizę kodu dla RuleSetSample**.  
  
2. Kliknij w oknie Lista błędów **ostrzeżenia** a następnie kliknij przycisk **opis** nagłówek kolumny, aby posortować ostrzeżenia alfanumerycznie.  
  
    W przypadku aplikacji rzeczywistych może rozwiązać ewentualne naruszenia reguły, warto na tym etapie ustalania, lub opcjonalnie wyłączyć lub pominąć reguły, jeśli można stwierdzić, że nie było warte ustalania. Aby uzyskać więcej informacji, zobacz [pomijanie ostrzeżeń przy użyciu atrybutu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3. Zwróć uwagę, CA1704 ostrzeżenia. Te naruszenia w tej regule wskazują, że "rozważ podanie bardziej zrozumiałej nazwy parametrów." Można rozwiązać ten problem w kodzie albo można wyłączyć reguły, zgodnie z opisem w następnej procedurze.  
  
   Następnie dostosujesz zestaw reguł, aby wykluczyć ostrzeżenie CA1704, "Identyfikatory powinny być zapisane poprawnie".  
  
#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Dostosowywanie zestawu w projekcie wyłączyć zasadę określonych reguł  
  
1. Na **analizy** menu, kliknij przycisk **Konfigurowanie analizy kodu dla RuleSetSample**.  
  
2. W **Uruchom ten zestaw reguł** listy rozwijanej liście, upewnij się, że **wszystkie reguły firmy Microsoft** reguły zestaw nadal jest wyróżniona, a następnie kliknij przycisk **Otwórz**. Zostanie wyświetlona strona zestawu reguł.  
  
3. Rozwiń węzeł kategorii Microsoft.Naming, a następnie wybierz ostrzeżenie CA1704.  
  
4. W obszarze **akcji** kolumny wybierz **None.** CA1704 uniemożliwia wyświetlanie jako ostrzeżenia lub błędu w oknie Lista błędów.  
  
    Teraz jest dobry moment, aby eksperymentować z różnymi przycisków paska narzędzi i opcji, aby zapoznać się z nimi filtrowania. Na przykład, można użyć **Group By** listy rozwijanej, aby pomóc w odnalezieniu daną regułę lub Kategoria reguły. Innym przykładem jest, że można użyć **Ukryj wyłączone reguły** przycisk na pasku narzędzi strony zestawu reguły, aby ukryć lub pokazać wszystkie reguły z **akcji** kolumna ustawiona **Brak**. Może to być przydatne, jeśli chcesz wyszukiwać wszystkich reguł, które została wyłączona, aby sprawdzić, czy nadal chcesz je wyłączyć.  
  
5. W menu Widok kliknij okno właściwości. Typ **Mój zestaw reguł niestandardowych** w polu Nazwa w oknie narzędzia właściwości. Spowoduje to zmianę nazwę wyświetlaną w nowy zestaw reguł [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.  
  
6. Na **pliku** menu, kliknij przycisk **Zapisz wszystkie Rules.ruleset Microsoft** Aby zapisać swoje dostosowanej reguły zestaw. Przejdź do folderu głównego projektu. W **FileName** polu tekstowym **MyCustomRuleSet**. Teraz można wybrać zestaw reguł niestandardowych do użytku z projektem.  
  
   Za pomocą Twojego nowego zestawu reguł utworzony masz teraz skonfigurować ustawienia projektu do określenia, czy chcesz użyć nowej reguły zestawu z nim.  
  
#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Określ nową regułę, ustawić do użytku z projektem  
  
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz **właściwości**.  
  
2. W **właściwości** kliknij pozycję **analizy kodu**.  
  
    W **Uruchom ten zestaw reguł** listy rozwijanej kliknij  **\<Przeglądaj... >**. Przejdź do folderu głównego projektu kodu, a następnie wybierz pozycję **MyCustomRuleSet.ruleset**. Jest to nowy zestaw reguł, który został utworzony w poprzedniej procedurze.  
  
3. Na **pliku** menu, kliknij przycisk **Zapisz** Aby zapisać konfigurację projektu. Teraz można niestandardowego zestawu reguł z projektem.  
  
   Na koniec uruchom analizę kodu ponownie przy użyciu zestawu reguł MyCustomRuleSet. Zwróć uwagę, czy okno listy błędów nie wyświetla naruszenie reguły wydajności CA1704.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Przeprowadź analizę kodu w projekcie RuleSetSample po raz drugi  
  
1. Na **analizy** menu, kliknij przycisk **Uruchom analizę kodu dla RuleSetSample**.  
  
2. W oknie Lista błędów, należy zauważyć, że po kliknięciu **ostrzeżenia**, nie są już wyświetlane CA1704 ostrzeżenie naruszenia reguły "Identyfikatory powinny być zapisane poprawnie".  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Informacje o zestawie reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md)
