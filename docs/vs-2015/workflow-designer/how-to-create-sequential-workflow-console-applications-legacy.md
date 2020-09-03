---
title: 'Instrukcje: Tworzenie aplikacji konsoli sekwencyjnego przepływu pracy (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662726"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Instrukcje: Tworzenie aplikacji konsoli sekwencyjnego przepływu pracy (starsza wersja)
Wykonaj następujące kroki, aby utworzyć projekt aplikacji konsolowej sekwencyjnego przepływu pracy przy użyciu starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] dostarczonej przez program [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy musisz być celem [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

### <a name="to-create-a-sequential-workflow-console-application"></a>Aby utworzyć aplikację konsolową sekwencyjnego przepływu pracy

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. Wybierz opcję **.NET Framework 3,0** lub opcję **.NET Framework 3,5** na liście rozwijanej w górnej części okna **Nowy projekt** , aby uzyskać dostęp do starszego projektanta.

    > [!NOTE]
    > Opcja domyślna w programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] jest **.NET Framework 4**. Ta opcja służy do tworzenia [!INCLUDE[wf](../includes/wf-md.md)] aplikacji przeznaczonych dla programu [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] i nie korzysta z starszego projektanta.

4. W okienku **typy projektów** wybierz pozycję projekty Visual C# lub projekty Visual Basic (w obszarze **inne języki**), a następnie wybierz pozycję **przepływ pracy**.

5. W okienku **Szablony** wybierz **kolejno pozycje sekwencyjna Aplikacja konsolowa**.

6. W polu **Nazwa** Wprowadź opisową nazwę projektu, aby ułatwić jego identyfikację.

7. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

     Zostanie otwarty Projektant formularzy systemu Windows i zostanie wyświetlony formularz Form1 utworzonego projektu.

8. Kliknij przycisk **OK**.

     Zostanie otwarty Projektant przepływu pracy i zostanie wyświetlona Powierzchnia projektu przepływu pracy sekwencyjnego, który został utworzony.

9. Przeciągnij działanie z **przybornika** do powierzchni projektowej w wyznaczonej sekcji **działania upuszczania** .

## <a name="see-also"></a>Zobacz też
 [Tworzenie starszych projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md) [opracowywanie przepływów](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301) pracy