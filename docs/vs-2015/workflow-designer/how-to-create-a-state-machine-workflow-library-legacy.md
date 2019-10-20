---
title: 'Instrukcje: Tworzenie biblioteki przepływu pracy automatu Stanów (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3cff5d6aaa28915524b7699affdf41d3bebef4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663376"
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Instrukcje: Tworzenie biblioteki przepływu pracy automatu Stanów (starsza wersja)
Wykonaj następujące kroki, aby utworzyć projekt biblioteki przepływu pracy automatu Stanów przy użyciu starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)] dostarczonej przez [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Użyj starszej [!INCLUDE[wfd2](../includes/wfd2-md.md)], jeśli chcesz wskazać [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-state-machine-workflow-library-project"></a>Aby utworzyć projekt biblioteki przepływu pracy automatu Stanów

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. Wybierz opcję **.NET Framework 3,0** lub opcję **.NET Framework 3,5** na liście rozwijanej w górnej części okna **Nowy projekt** , aby uzyskać dostęp do starszego projektanta.

    > [!NOTE]
    > Opcja domyślna w [!INCLUDE[vs2010](../includes/vs2010-md.md)] jest **.NET Framework 4**. Ta opcja służy do tworzenia aplikacji [!INCLUDE[wf](../includes/wf-md.md)] przeznaczonych dla [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] i nie korzysta z starszego projektanta.

4. W okienku **typy projektów** wybierz pozycję Wizualizacja C# lub Visual Basic (w obszarze **inne języki**), a następnie wybierz pozycję **przepływ pracy**.

5. W okienku **Szablony** wybierz pozycję **Biblioteka przepływu pracy automatu Stanów**.

6. W polu **Nazwa** Wprowadź opisową nazwę projektu, aby ułatwić jego identyfikację.

7. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

     Jeśli chcesz utworzyć katalog rozwiązania dla projektu, zaznacz pole wyboru **Utwórz katalog dla rozwiązania** i wprowadź nazwę w polu **Nazwa rozwiązania** .

8. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 [Tworzenie starszych projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md) — [przepływy pracy automatu Stanów](https://msdn.microsoft.com/library/344caacd-bf3b-4716-bd5a-eca74fc5a61d)