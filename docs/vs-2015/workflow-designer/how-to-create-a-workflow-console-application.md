---
title: 'Instrukcje: Tworzenie aplikacji konsoli przepływu pracy | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a436027fc4194f762fc4b28545fdf5d4bd3b95b6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444614"
---
# <a name="how-to-create-a-workflow-console-application"></a>Instrukcje: Tworzenie aplikacji konsoli przepływu pracy
[!INCLUDE[wf](../includes/wf-md.md)] Umożliwia tworzenie przepływów pracy na potrzeby wykonywania systemu lub procesów przez ludzi. [!INCLUDE[wfd1](../includes/wfd1-md.md)] Udostępnia na powierzchnię projektową do tworzenia tych przepływów pracy. [!INCLUDE[wfd2](../includes/wfd2-md.md)] Może służyć do tworzenia przepływów pracy z poziomu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub może być zintegrowane do innych aplikacji, których ponowne hostowanie projektanta.  
  
 W tym temacie opisano sposób użycia [!INCLUDE[wfd2](../includes/wfd2-md.md)] w [!INCLUDE[vs2010](../includes/vs2010-md.md)] Tworzenie przepływu pracy w aplikacji konsoli.  
  
### <a name="to-create-a-workflow-console-application"></a>Do tworzenia aplikacji konsolowej przepływu pracy  
  
1. Rozpocznij [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. Na **pliku** menu wskaż **New**, a następnie wybierz pozycję **projektu...** .  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3. W **zainstalowane szablony** okienku wybierz **przepływu pracy** albo **Visual C#** lub **języka Visual Basic** grupowania, w zależności od usługi język preferencji.  
  
4. W środkowym okienku wybierz **Aplikacja konsoli przepływu pracy**.  
  
5. W **nazwa** wprowadź opisową nazwę projektu ułatwić identyfikowanie.  
  
6. W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.  
  
7. W **rozwiązania** wprowadź nazwę dla nowego rozwiązania. Kliknij przycisk **OK** do tworzenia aplikacji.  
  
    > [!NOTE]
    > Jeśli chcesz dodać aplikację konsoli przepływu pracy do istniejącego rozwiązania, otwórz rozwiązanie w [!INCLUDE[vs2010](../includes/vs2010-md.md)], kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj**, następnie  **Nowy projekt...** Aby otworzyć **nowy projekt** okno dialogowe. Należy postępować zgodnie z powyższym opisem w tej procedurze.  
  
8. Szablon projektu umożliwia utworzenie definicji przepływu pracy w XAML i definicji aplikacji konsoli jest w kodzie źródłowym. [!INCLUDE[wfd2](../includes/wfd2-md.md)] Otwiera i wyświetla obszar roboczy został utworzony przepływ pracy.  
  
9. Do tworzenia przepływu pracy, przeciągnij działania lub inne elementy przepływu pracy z **przybornika** do powierzchni projektowej w przepływie pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)