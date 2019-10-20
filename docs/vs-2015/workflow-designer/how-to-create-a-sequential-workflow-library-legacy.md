---
title: 'Instrukcje: Tworzenie biblioteki sekwencyjnego przepływu pracy (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: adc2e71678e6892d12640a3153f24bfb90dfa429
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663398"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Instrukcje: Tworzenie biblioteki sekwencyjnego przepływu pracy (starsza wersja)
Wykonaj następujące kroki, aby utworzyć projekt biblioteki sekwencyjnego przepływu pracy przy użyciu starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)] dostarczonej przez [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Użyj starszej [!INCLUDE[wfd2](../includes/wfd2-md.md)], jeśli chcesz wskazać [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-sequential-workflow-library-project"></a>Aby utworzyć projekt biblioteki sekwencyjnego przepływu pracy

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. Wybierz opcję **.NET Framework 3,0** lub opcję **.NET Framework 3,5** na liście rozwijanej w górnej części okna **Nowy projekt** , aby uzyskać dostęp do starszego projektanta.

    > [!NOTE]
    > Opcja domyślna w [!INCLUDE[vs2010](../includes/vs2010-md.md)] jest **.NET Framework 4**. Ta opcja służy do tworzenia aplikacji [!INCLUDE[wf](../includes/wf-md.md)] przeznaczonych dla [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] i nie korzysta z starszego projektanta.

4. W okienku **typy projektów** wybierz pozycję Wizualizacja C# lub Visual Basic (w obszarze **inne języki**), a następnie wybierz pozycję **przepływ pracy**.

5. W okienku **Szablony** wybierz **kolejno pozycje Biblioteka sekwencyjnego przepływu pracy**.

6. W polu **Nazwa** Wprowadź opisową nazwę projektu, aby ułatwić jego identyfikację.

7. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

     Jeśli chcesz utworzyć katalog rozwiązania dla projektu, zaznacz pole wyboru **Utwórz katalog dla rozwiązania** i wprowadź nazwę w polu **Nazwa rozwiązania** .

8. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 [Tworzenie starszych projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md) — [Style tworzenia przepływu pracy](https://msdn.microsoft.com/aacf4ec6-da05-4974-958a-974769dda739)