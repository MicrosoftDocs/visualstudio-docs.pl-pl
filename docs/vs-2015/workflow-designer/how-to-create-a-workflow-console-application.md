---
title: 'Instrukcje: Tworzenie aplikacji konsolowej przepływu pracy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1334655f2a8b8587922628664e43784b54ce971
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604917"
---
# <a name="how-to-create-a-workflow-console-application"></a>Instrukcje: Tworzenie aplikacji konsoli przepływu pracy
[!INCLUDE[wf](../includes/wf-md.md)] umożliwia tworzenie przepływów pracy na potrzeby wykonywania procesów systemowych lub ludzkich. [!INCLUDE[wfd1](../includes/wfd1-md.md)]Zapewnia powierzchnię projektowania do tworzenia tych przepływów pracy. [!INCLUDE[wfd2](../includes/wfd2-md.md)]Może służyć do tworzenia przepływów pracy z poziomu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub można go zintegrować z innymi aplikacjami, które ponownie obsługują projektanta.

 W tym temacie opisano sposób użycia programu [!INCLUDE[wfd2](../includes/wfd2-md.md)] w programie w [!INCLUDE[vs2010](../includes/vs2010-md.md)] celu utworzenia przepływu pracy w aplikacji konsolowej.

### <a name="to-create-a-workflow-console-application"></a>Aby utworzyć aplikację konsolową przepływu pracy

1. Rozpocznij [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt...**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. W okienku **zainstalowane szablony** wybierz **przepływ pracy** z grup **Visual C#** lub **Visual Basic** , w zależności od języka preferencji.

4. W środkowym okienku wybierz pozycję **aplikacja konsoli przepływu pracy**.

5. W polu **Nazwa** Wprowadź opisową nazwę projektu, aby ułatwić jego identyfikację.

6. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

7. W polu **rozwiązanie** wprowadź nazwę nowego rozwiązania. Kliknij przycisk **OK** , aby utworzyć aplikację.

    > [!NOTE]
    > Jeśli chcesz dodać aplikację konsoli przepływu pracy do istniejącego rozwiązania, Otwórz to rozwiązanie w programie, kliknij [!INCLUDE[vs2010](../includes/vs2010-md.md)] prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj**, a następnie **Nowy projekt...** Aby otworzyć okno dialogowe **Nowy projekt** . Postępuj zgodnie z powyższym opisem w tej procedurze.

8. Szablon projektu tworzy definicję przepływu pracy w języku XAML, a definicja aplikacji konsolowej znajduje się w kodzie źródłowym. [!INCLUDE[wfd2](../includes/wfd2-md.md)]Zostanie otwarta i zostanie wyświetlona Kanwa utworzonego przepływu pracy.

9. Aby utworzyć przepływ pracy, przeciągnij działania lub inne elementy przepływu pracy z **przybornika** do powierzchni projektowej w przepływie pracy.

## <a name="see-also"></a>Zobacz też
 [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)