---
title: 'Instrukcje: Synchronizowanie zestawów reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 32558f746745fdcb717aa7c218f996924418ae79
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082051"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Instrukcje: Synchronizowanie zestawów reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia analizy kodu dla projektów kodu zasad ewidencjonowania dla projektu zespołowego można zsynchronizować, określając zestaw reguł, który zawiera co najmniej reguły, które są określone w regule ustawić dla zasad ewidencjonowania. Potencjalnych klientów usługi dla deweloperów może poinformować Cię o nazwę i lokalizację zestawu reguł dla zasad ewidencjonowania. Aby upewnić się, że analiza kodu dla projektu używa poprawny zestaw reguł, można użyć jednej z następujących opcji:  
  
- Zasady ewidencjonowania korzysta z jednego z Microsoft wbudowany zestaw reguł, Otwórz okno dialogowe właściwości dla projektu kodu, wyświetlenia strony analizy kodu i wybierz regułę, ustawić na stronie analizy kodu w ustawieniach projektu kodu. Microsoft standardowych zestawów reguł są automatycznie instalowane z programem Visual Studio są ustawione na tylko do odczytu i nie można edytować. Jeśli zestawy reguł nie są edytowane, gwarancję reguł w zasadzie i zestawów reguł lokalnych do dopasowania.  
  
- Jeśli zasady ewidencjonowania używa niestandardowego zestawu reguł, należy wykonać operację pobrania w pliku zestawu reguł w kontroli wersji, aby utworzyć kopię lokalną. Następnie można określić lokalizacji lokalnej w ustawienia analizy kodu dla projektu kodu. Reguły są gwarantowane do dopasowania, jeśli zestaw reguł dla zasad ewidencjonowania jest aktualny.  
  
     Jeśli mapujesz lokalizację kontroli wersji do lokalnego folderu, który znajduje się w tej samej relacji do katalogu głównego projektu zespołowego jako projekt kodu lokalizacji reguły można ustawić za pomocą ścieżki względnej. Ścieżka względna gwarantuje, że ustawienie projektu kodu do analizy kodu mogą być przenoszone do innych komputerów.  
  
- Dostosuj kopię zestawu reguł dla zasad ewidencjonowania dla projektu kodu. Upewnij się, że nowy zestaw reguł zawiera wszystkie reguły w zasadach ewidencjonowania i innymi regułami, które mają zostać uwzględnione. Upewnij się, że Twoje zestaw reguł zawiera wszystkie reguły w regule ustawić dla zasad ewidencjonowania.  
  
### <a name="to-specify-a-microsoft-standard-rule-set"></a>Aby określić regułę standard firmy Microsoft należy ustawić  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij przycisk **właściwości**.  
  
2. Kliknij przycisk **analiza kodu**.  
  
3. W **Uruchom ten zestaw reguł** kliknij zestaw reguł zasad ewidencjonowania.  
  
### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Aby określić zestaw reguł niestandardowych zasad ewidencjonowania  
  
1. Jeśli to konieczne, należy wykonać operację pobrania w pliku zestawu reguł, który określa zasady ewidencjonowania.  
  
2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt kodu, a następnie kliknij przycisk **właściwości**.  
  
3. Kliknij przycisk **analiza kodu**.  
  
4. W **Uruchom ten zestaw reguł** kliknij  **\<Przeglądaj … >**.  
  
5. W **Otwórz** okna dialogowego wprowadź plik zestawu reguł zasad ewidencjonowania.  
  
### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Aby utworzyć regułę niestandardową należy ustawić dla projektu kodu  
  
1. Wykonaj jedną z procedur we wcześniejszej części tego tematu, aby wybrać zasady ewidencjonowania projektu zespołowego na stronie analizy kodu w oknie dialogowym Ustawienia projektu.  
  
2. Kliknij przycisk **Otwórz**.  
  
3. Dodawanie lub usuwanie reguł za pomocą edytora zestawu reguł.  
  
     Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4. Zapisz zmodyfikowano regułę, Ustaw plik .ruleset, na komputerze lokalnym lub ścieżką UNC.  
  
5. Otwórz okno dialogowe właściwości dla projektu kodu, a następnie wyświetlić **analizy kodu** strony.  
  
6. W **Uruchom ten zestaw reguł** kliknij  **\<Przeglądaj … >**.  
  
7. W **Otwórz** okna dialogowego wprowadź plik zestawu reguł.
