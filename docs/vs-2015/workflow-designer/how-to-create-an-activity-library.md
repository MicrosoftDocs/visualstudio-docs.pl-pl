---
title: 'Instrukcje: Tworzenie biblioteki działań | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662756"
---
# <a name="how-to-create-an-activity-library"></a>Instrukcje: Tworzenie biblioteki działań
Działania niestandardowe służą do modelowania określonych procesów biznesowych w przepływie pracy. Podano szablon biblioteki działań w programie, [!INCLUDE[vs2010](../includes/vs2010-md.md)] który umożliwia tworzenie takich niestandardowych działań wizualnie przy użyciu [!INCLUDE[wfd1](../includes/wfd1-md.md)] .

### <a name="to-create-a-workflow-activity-library"></a>Aby utworzyć bibliotekę działań przepływu pracy

1. Rozpocznij [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt...**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. W okienku **typy projektów** wybierz opcję **przepływ pracy** z projektów **Visual C#** lub grupowania **Visual Basic** w zależności od preferencji językowych.

4. W okienku **Szablony** wybierz pozycję **Biblioteka działań**.

5. W polu **Nazwa** wpisz opisową nazwę projektu, aby ułatwić jego identyfikację.

6. W polu **Lokalizacja** wpisz katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

7. W polu **rozwiązanie** wpisz nazwę opisową rozwiązania, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli chcesz dodać aplikację konsoli przepływu pracy do istniejącego rozwiązania, Otwórz to rozwiązanie w programie, kliknij [!INCLUDE[vs2010](../includes/vs2010-md.md)] prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj**, a następnie **Nowy projekt...** Aby otworzyć okno dialogowe **Nowy projekt** . Postępuj zgodnie z powyższym opisem w tej procedurze.

8. Szablon projektu tworzy definicję działania w języku XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] otwiera i wyświetla kanwę dla działania niestandardowego.

9. Przeciągnij działanie z **przybornika** na powierzchnię projektu, aby uwzględnić je w działaniu niestandardowym.

    > [!CAUTION]
    > W treści działania niestandardowego można używać tylko jednego działania podrzędnego. jednak działanie podrzędne może być działaniem złożonym, takim jak <xref:System.Activities.Statements.Sequence> działanie lub <xref:System.Activities.Statements.Flowchart> działanie.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: tworzenie działania](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [tworzenia projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)