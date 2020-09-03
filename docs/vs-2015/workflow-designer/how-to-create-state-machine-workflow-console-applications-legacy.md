---
title: 'Instrukcje: Tworzenie aplikacji konsoli przepływu pracy automatu Stanów (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 48c7e06c2cb0e59de754b1ab36b693c4c9872985
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662718"
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Instrukcje: Tworzenie aplikacji konsoli przepływu pracy automatu stanów (starsza wersja)
Wykonaj następujące kroki, aby utworzyć projekt aplikacji konsoli przepływu pracy automatu Stanów przy użyciu starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] dostarczonej przez program [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy musisz być celem [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

### <a name="to-create-a-state-machine-application-project"></a>Aby utworzyć projekt aplikacji automatu Stanów

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. Wybierz opcję **.NET Framework 3,0** lub opcję **.NET Framework 3,5** na liście rozwijanej w górnej części okna **Nowy projekt** , aby uzyskać dostęp do starszego projektanta.

    > [!NOTE]
    > Opcja domyślna w programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] jest **.NET Framework 4**. Ta opcja służy do tworzenia [!INCLUDE[wf](../includes/wf-md.md)] aplikacji przeznaczonych dla programu [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] i nie korzysta z starszego projektanta.

4. W okienku **typy projektów** wybierz pozycję Visual C# lub Visual Basic (w obszarze **inne języki**), a następnie wybierz pozycję **przepływ pracy**.

5. W okienku **Szablony** wybierz pozycję **stan Aplikacja konsolowa przepływ pracy**.

6. W polu **Nazwa** Wprowadź opisową nazwę projektu, aby ułatwić jego identyfikację.

7. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

     Jeśli chcesz utworzyć katalog rozwiązania dla projektu, zaznacz pole wyboru **Utwórz katalog dla rozwiązania** i wprowadź nazwę w polu **Nazwa rozwiązania** .

8. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 [Tworzenie starszych projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md) [: Tworzenie biblioteki przepływu pracy automatu Stanów (starsza wersja)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)