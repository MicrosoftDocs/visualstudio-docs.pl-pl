---
title: 'Instrukcje: Tworzenie lub aktualizowanie standardowych zasad analizy kodu ewidencjonowania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b1ad310385d5c8c8cecaee408d049a172d53e1e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436852"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Instrukcje: Tworzenie lub aktualizowanie standardowych zasad ewidencjonowania analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wymagać, można uruchomić analizę kodu dla wszystkich projektów kodu w projekcie zespołowym w przy użyciu zasady analizy kodu ewidencjonowania. Wymaga analizy kodu może poprawić jakość kodu, który jest ewidencjonowany w kodzie podstawowym.  
  
> [!NOTE]
> Ta funkcja jest dostępna tylko wtedy, gdy używasz Team Foundation Server.  
  
 Zasady ewidencjonowania analizy kodu są ustawiane w ustawieniach projektu zespołowego i mają zastosowanie do każdego projektu kodu w projekcie zespołowym. Przebiegi analizy kodu są skonfigurowane dla projektów kodu w pliku projektu (.xxproj) dla projektu kodu. Przebiegi analizy kodu są wykonywane na komputerze lokalnym. Po włączeniu zasad analizy kodu ewidencjonowania, muszą być skompilowane pliki w projekcie kodu, które mają być sprawdzane po ich ostatniej modyfikacji i uruchomienia analizy kodu zwrócić, zawiera co najmniej reguły w ustawieniach projektu zespołowego, należy wykonać na komputerze, gdzie c zmiany zostały wprowadzone.  
  
- Dla kodu zarządzanego, Ustaw zasady ewidencjonowania, określając *zestaw reguł* zawierającą podzbiór reguł analizy kodu.  
  
- Dla kodu C/C++ zasad ewidencjonowania wymaga, że są uruchomione wszystkie reguły analizy kodu. Możesz dodać wstępne procesora dyrektywy można wyłączyć określone zasady dla poszczególnych projektów kodu w projekcie zespołowym.  
  
  Po określeniu zasad ewidencjonowania dla kodu zarządzanego, członkowie zespołu mogą wykonywać synchronizację z ich ustawienia analizy kodu dla projektów kodu, aby ustawienia zasad projektu zespołowego.  
  
### <a name="to-open-the-check-in-policy-editor"></a>Aby otworzyć Edytor zasad ewidencjonowania  
  
1. W programie Team Explorer, kliknij prawym przyciskiem myszy nazwę projektu zespołowego, wskaż opcję **ustawienia projektu zespołowego**, a następnie kliknij przycisk **kontroli źródła**.  
  
2. W **kontroli źródła** okno dialogowe, wybierz opcję **zasad ewidencjonowania** kartę.  
  
3. Wykonaj jedną z następujących czynności:  
  
    - Kliknij przycisk **Dodaj** do tworzenia nowych zasad ewidencjonowania.  
  
    - Kliknij dwukrotnie istniejące **analizy kodu** pozycja **typ zasad** listy, aby zmienić zasady.  
  
### <a name="to-set-policy-options"></a>Aby ustawić opcje zasad  
  
- Zaznacz lub wyczyść następujące opcje:  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |**Wymuszanie zaewidencjonowanie obejmowało tylko pliki, które są częścią bieżącego rozwiązania.**|Analiza kodu można uruchomić tylko na pliki określone w plikach konfiguracji rozwiązania i projektu. Te zasady gwarantuje, że cały kod, który jest częścią rozwiązania są analizowane.|  
    |**Wymuszanie analiza kodu C/C++ (/ analyze)**|Wymaga się, że wszystkie projekty C lub C++ być kompilowany / analyze — opcja kompilatora do uruchamiania analizy kodu, zanim może zostać sprawdzone.|  
    |**Wymuszanie analizy kodu dla kodu zarządzanego**|Wymaga wszystkich zarządzanych projektów uruchamiania analizy kodu i kompilacji, zanim może zostać sprawdzone.|  
  
- 
  
### <a name="to-specify-a-managed-rule-set"></a>Aby określić zestaw reguł zarządzanych  
  
- Z **Uruchom ten zestaw reguł** listy, użyj jednej z następujących metod:  
  
    - Wybierz zestaw standardowych reguł firmy Microsoft.  
  
    - Aby wybrać niestandardowego zestawu reguł, kliknij przycisk  **\<wybierz zestaw reguł z kontroli źródła... >** , a następnie wpisz ścieżkę kontroli wersji, reguły, ustaw w przeglądarce kontroli źródła. Składnia ścieżki kontroli wersji jest następująca:  
  
    - **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    - Aby uzyskać więcej informacji o sposobie tworzenia i wdrażania reguły niestandardowe zasady ewidencjonowania, zobacz [Implementowanie niestandardowych zaewidencjonowania zasad dla zarządzanego kodu](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
