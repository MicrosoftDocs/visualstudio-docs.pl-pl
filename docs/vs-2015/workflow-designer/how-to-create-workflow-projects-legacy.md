---
title: 'Instrukcje: Tworzenie projektów przepływu pracy (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf68c1a28f662bfa4e271d3c402ef1c8946b6f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668681"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Instrukcje: Tworzenie projektów przepływu pracy (starsza wersja)
Wykonaj następujące kroki, aby utworzyć [!INCLUDE[wf](../includes/wf-md.md)] projekt, który jest przeznaczony dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] . Ta procedura korzysta ze starszej wersji programu [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

### <a name="to-create-a-workflow-project"></a>Aby utworzyć projekt przepływu pracy

1. Rozpocznij [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. Wybierz opcję **.NET Framework 3,0** lub opcję **.NET Framework 3,5** na liście rozwijanej w górnej części okna **Nowy projekt** , aby uzyskać dostęp do starszego projektanta.

    > [!NOTE]
    > Opcja domyślna w programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] jest **.NET Framework 4**. Ta opcja służy do tworzenia [!INCLUDE[wf](../includes/wf-md.md)] aplikacji przeznaczonych dla programu [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] i nie korzysta z starszego projektanta.

4. W okienku **typy projektów** wybierz pozycję projekty Visual C# lub Visual Basic projekty, a następnie wybierz pozycję **przepływ pracy**.

5. W okienku **Szablony** wybierz jeden z zainstalowanych szablonów projektu:

    - Aplikacja konsolowa sekwencyjnego przepływu pracy

    - Biblioteka sekwencyjnego przepływu pracy

    - Biblioteka działań przepływu pracy

    - Aplikacja konsolowa przepływu pracy automatu Stanów

    - Biblioteka przepływu pracy automatu Stanów

    - Pusty projekt przepływu pracy

6. W polu **Nazwa** Wprowadź opisową nazwę projektu, aby ułatwić jego identyfikację.

7. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do katalogu.

     Jeśli chcesz utworzyć katalog rozwiązania dla projektu, zaznacz pole wyboru **Utwórz katalog dla rozwiązania** i wprowadź nazwę w polu **Nazwa rozwiązania** .

8. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 [Tworzenie starszej wersji projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md)