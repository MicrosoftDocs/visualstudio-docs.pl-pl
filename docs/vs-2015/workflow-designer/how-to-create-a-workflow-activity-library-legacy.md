---
title: 'Instrukcje: Tworzenie biblioteki działań przepływu pracy (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5bc4566c1ea520ac1050227ac8e4c0aee22e617
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604961"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Instrukcje: Tworzenie biblioteki działań przepływów pracy (starsza wersja)
Wykonaj następujące kroki, aby utworzyć projekt biblioteki działań przepływu pracy przy użyciu starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] dostarczonej przez program [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy musisz być celem [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

### <a name="to-create-a-workflow-activity-library-project"></a>Aby utworzyć projekt biblioteki działań przepływu pracy

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. Wybierz opcję **.NET Framework 3,0** lub opcję **.NET Framework 3,5** na liście rozwijanej w górnej części okna **Nowy projekt** , aby uzyskać dostęp do starszego projektanta.

    > [!NOTE]
    > Opcja domyślna w programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] jest **.NET Framework 4**. Ta opcja służy do tworzenia [!INCLUDE[wf](../includes/wf-md.md)] aplikacji przeznaczonych dla programu [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] i nie korzysta z starszego projektanta.

4. W okienku **typy projektów** wybierz pozycję Visual C# lub Visual Basic (w obszarze **inne języki**), a następnie wybierz pozycję **przepływ pracy**.

5. W okienku **Szablony** wybierz pozycję **Biblioteka działań przepływu pracy**.

6. W polu **Nazwa** Wprowadź opisową nazwę projektu, aby ułatwić jego identyfikację.

7. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

     Jeśli chcesz utworzyć katalog rozwiązania dla projektu, zaznacz pole wyboru **Utwórz katalog dla rozwiązania** i wprowadź nazwę w polu **Nazwa rozwiązania** .

8. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 [Tworzenie starszych projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md) [przy użyciu starszych](../workflow-designer/using-the-legacy-activity-designer.md) działań [starszych przepływów pracy](../workflow-designer/legacy-workflow-activities.md) projektanta działań [opracowywanie działań przepływu pracy](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52) [Windows Workflow Foundation działań](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)