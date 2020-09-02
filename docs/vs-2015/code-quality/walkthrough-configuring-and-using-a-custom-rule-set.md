---
title: 'Przewodnik: Konfigurowanie niestandardowego zestawu reguł i korzystanie z niego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645739"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Wskazówki: konfigurowanie niestandardowego zestawu reguł i korzystanie z niego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak używać narzędzi analizy kodu, które zostały skonfigurowane do używania niestandardowego *zestawu reguł* w bibliotece klas. Można wybrać zestaw reguł, który odnosi się do typu projektu określonego dla danego rozwiązania, lub wybrać alternatywne zestawy reguł, aby spełnić konkretne zapotrzebowanie, takie jak skanowanie starszego kodu pod kątem problemów, które mogą zostać naprawione w sposób niepowodujący przerwania. W obu przypadkach zestawy reguł można także dostosować, aby dostosować je do wymagań projektu.

 W tym instruktażu przedstawiono następujące procesy:

- Utwórz bibliotekę klas.

- Wybierz zestaw reguł analizy kodu dla **podstawowych zasad wytycznych dotyczących projektowania firmy Microsoft** .

- Dodaj własny kod do klasy.

- Uruchom analizę kodu.

- Dostosuj zestaw reguł.

- Uruchom analizę kodu i zobacz, jak działa zachowanie dostosowywania zestawu reguł.

## <a name="prerequisites"></a>Wymagania wstępne

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] lub [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>Używanie zestawów reguł z analizą kodu
 Najpierw utwórz prostą bibliotekę klas.

#### <a name="create-a-class-library"></a>Tworzenie biblioteki klas

1. W menu **plik** kliknij pozycję **Nowy** , a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** w obszarze **typy projektów**kliknij pozycję **Visual C#**.

3. W obszarze **Visual C#** wybierz pozycję **Biblioteka klas**.

4. W polu tekstowym **Nazwa** wpisz **RuleSetSample** , a następnie kliknij przycisk **OK**.

   Następnie wybierz zestaw reguł **podstawowych wytycznych dotyczących projektowania firmy Microsoft** i Zapisz go w projekcie.

#### <a name="select-a-code-analysis-rule-set"></a>Wybierz zestaw reguł analizy kodu

1. W menu **Analizuj** kliknij polecenie **Konfiguruj analizę kodu dla RuleSetSample**.

    Zostaną wyświetlone ustawienia konfiguracji dotyczące analizy kodu.

2. Z listy rozwijanej **Uruchom ten zestaw reguł** wybierz pozycję **Microsoft wszystkie reguły**.

    Aby uzyskać więcej informacji na temat dostępnych zestawów reguł, zobacz [Dokumentacja zestawu reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md).

    W menu plik kliknij polecenie **Zapisz wybrane elementy** , aby zaktualizować plik projektu o informacje o wybranym zestawie reguł i jego ustawieniach.

   > [!TIP]
   > W przypadku rzeczywistej sytuacji dobrą metodą określania priorytetu problemów, które mają zostać użyte do analizy kodu, jest rozpoczęcie od **minimalnych zalecanych reguł** zestawu reguł i skorygowanie potrzebnych problemów, a następnie przyrostowe dodanie większej liczby reguł lub zestawów reguł w celu znalezienia i rozwiązania dodatkowych problemów.

   Następnie dodasz kod do biblioteki klas, która zostanie użyta do zademonstrowania naruszeń identyfikatorów CA1704 "w kodzie". Aby uzyskać więcej informacji, zobacz [CA1704: Identyfikatory powinny być poprawnie napisane](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

#### <a name="add-your-own-code"></a>Dodaj własny kod

- W Eksplorator rozwiązań otwórz plik Class1.cs i Zastąp istniejący kod następującym kodem:

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

  Teraz można uruchomić analizę kodu w projekcie RuleSetSample i poszukać błędów i ostrzeżeń generowanych w oknie Lista błędów.

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Uruchom analizę kodu w projekcie RuleSetSample

1. W menu **Analizuj** kliknij polecenie **Uruchom analizę kodu w witrynie RuleSetSample**.

2. W oknie Lista błędów kliknij pozycję **ostrzeżenia** , a następnie kliknij nagłówek kolumny **Opis** , aby posortować ostrzeżenia alfanumerycznie.

    W aplikacji rzeczywistej można naprawić wszystkie naruszenia zasad w tym momencie, lub opcjonalnie wyłączyć lub pominąć regułę, jeśli okaże się, że nie Naprawiono tego problemu. Aby uzyskać więcej informacji, zobacz [pomijanie ostrzeżeń przy użyciu atrybutu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

3. Zwróć uwagę na ostrzeżenia CA1704. Te naruszenia zasad wskazują, że należy "rozważyć podanie bardziej zrozumiałej nazwy parametrów". Możesz rozwiązać ten problem w kodzie lub wyłączyć regułę, zgodnie z opisem w następnej procedurze.

   Następnie dostosuj zestaw reguł, aby wykluczyć ostrzeżenie CA1704, "Identyfikatory powinny być poprawnie napisane".

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Dostosuj zestaw reguł dla projektu, aby wyłączyć określoną regułę

1. W menu **Analizuj** kliknij polecenie **Konfiguruj analizę kodu dla RuleSetSample**.

2. Na liście rozwijanej **Uruchom ten zestaw reguł** Sprawdź, czy zestaw reguł **Microsoft All Rules** jest nadal wyróżniony, a następnie kliknij przycisk **Otwórz**. Zostanie wyświetlona strona zestaw reguł.

3. Rozwiń węzeł kategorii Microsoft. nazwa, a następnie wybierz ostrzeżenie CA1704.

4. W kolumnie **Akcja** wybierz opcję **Brak.** Zapobiega to wyświetlaniu CA1704 jako ostrzeżenia lub błędu w oknie Lista błędów.

    Teraz warto eksperymentować z różnymi przyciskami paska narzędzi i opcjami filtrowania, aby zapoznać się z nimi. Na przykład można użyć listy rozwijanej **Grupuj według** , aby pomóc w lokalizowaniu określonej reguły lub kategorii reguł. Innym przykładem jest to, że można użyć przycisku **Ukryj wyłączone reguły** na pasku narzędzi strony zestawu reguł, aby ukryć lub pokazać wszystkie reguły z kolumną **Akcja** ustawione na **Brak**. Może to być przydatne, jeśli chcesz skanować w poszukiwaniu reguł, które zostały wyłączone w celu zweryfikowania, że nadal chcesz je wyłączyć.

5. W menu Widok kliknij okno właściwości. W polu Nazwa okna narzędzia właściwości wpisz **mój niestandardowy zestaw reguł** . Spowoduje to zmianę nazwy wyświetlanej nowego zestawu reguł w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.

6. W menu **plik** kliknij polecenie **Zapisz Microsoft All rules.** reguł, aby zapisać dostosowany zestaw reguł. Przejdź do folderu głównego projektu. W polu tekstowym **Nazwa pliku** wpisz **MyCustomRuleSet**. Niestandardowy zestaw reguł można teraz wybrać do użycia z projektem.

   Po utworzeniu nowego zestawu reguł teraz musisz skonfigurować ustawienia projektu, aby określić, że chcesz użyć nowego zestawu reguł.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Określ nowy zestaw reguł do użycia z projektem

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**.

2. Na karcie **Właściwości** kliknij pozycję **Analiza kodu**.

    Na liście rozwijanej **Uruchom ten zestaw reguł** kliknij pozycję **\<Browse..>** . Przejdź do folderu głównego projektu kodu, a następnie wybierz **MyCustomRuleSet. zestaw reguł**. To jest nowy zestaw reguł, który został utworzony w poprzedniej procedurze.

3. W menu **plik** kliknij polecenie **Zapisz** , aby zapisać konfigurację projektu. Niestandardowy zestaw reguł może być teraz używany z projektem.

   Na koniec ponownie uruchomimy analizę kodu przy użyciu zestawu reguł MyCustomRuleSet. Zwróć uwagę, że okno Lista błędów nie wyświetla naruszenia reguły wydajności CA1704.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Uruchom analizę kodu w projekcie RuleSetSample po raz drugi

1. W menu **Analizuj** kliknij polecenie **Uruchom analizę kodu w witrynie RuleSetSample**.

2. W oknie Lista błędów Zwróć uwagę, że po kliknięciu przycisku **ostrzeżenia**nie widzisz już CA1704 naruszeń ostrzeżeń dotyczących zasad "Identyfikatory powinny mieć poprawną wartość".

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Konfigurowanie analizy kodu dla odwołania do](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [zestawu reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md) projektu zarządzanego
