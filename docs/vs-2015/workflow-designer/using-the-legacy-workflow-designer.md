---
title: Używanie starszej Projektant przepływu pracy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2fa11cd0b29f3b8ee6008b8c0b3369b16812f0e5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302784"
---
# <a name="using-the-legacy-workflow-designer"></a>Używanie starszej wersji Projektanta przepływu pracy
Starsze [!INCLUDE[wfd2](../includes/wfd2-md.md)] dostarczone przez [!INCLUDE[vs2010](../includes/vs2010-md.md)] mogą służyć jako element docelowy [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Dostęp do niego można uzyskać, wybierając opcję **.NET Framework 3,0** lub opcję **.NET Framework 3,5** na liście rozwijanej w górnej części okna **Nowy projekt** . Opcja domyślna w [!INCLUDE[vs2010](../includes/vs2010-md.md)] jest **.NET Framework 4** , który służy do tworzenia aplikacji [!INCLUDE[wf](../includes/wf-md.md)] przeznaczonych dla [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] zapewnia sposób graficznego tworzenia aplikacji [!INCLUDE[wf](../includes/wf-md.md)] przy użyciu znanego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu użytkownika. [!INCLUDE[wf](../includes/wf-md.md)] aplikacje składają się z kroków procesu przepływu pracy o nazwie Activities. Aby utworzyć przepływ pracy, Zredaguj działania na powierzchni projektowej, przeciągając odpowiednie Projektanci działań z **przybornika** na powierzchnię projektu.

 W poniższej tabeli wymieniono najważniejsze funkcje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Windows Workflow Foundation.

|Funkcja|Opis|
|-------------|-----------------|
|Przeciąganie i upuszczanie działania|Przeciągnij działania z **przybornika** na powierzchnię projektu, aby utworzyć przepływ pracy.|
|Przeglądarka właściwości|Standardowe okno **Właściwości** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] służy do konfigurowania właściwości działania.|
|Powiększenie|Ikona **poziomu powiększenia** ze zmianami jest umieszczona pod pionowym paskiem przewijania po prawej stronie powierzchni projektowej. Kliknij przycisk "niezgodne" i wybierz procent powiększenia, aby spowodować Powiększanie lub pomniejszanie grafiki przepływu pracy. Możesz również użyć ikony **kadrowania** , aby powiększyć i pomniejszyć.|
|Panoramowanie|Ikona **kadrowania** , okrąg zawierający cztery przecinające się strzałki wskazujące cztery kierunki, znajduje się poniżej pionowego paska przewijania po prawej stronie powierzchni projektowej tuż poniżej ikony powiększenia ze zmianami. Jeśli klikniesz ikonę kadrowania, menu rozwijane oferuje następujące opcje dotyczące kursora:<br /><br /> — **Powiększanie** kursora lupy umożliwia powiększanie przez kliknięcie powierzchni projektowej.<br />— Kursor lupy z powiększanymi **powiększeniami** pozwala pomniejszać, klikając powierzchnię projektu.<br />-Kursor **Narzędzia do nawigacji** umożliwia "Przechwyć" i przechodzenie do widoku przepływu pracy na powierzchni projektowej.<br />— **Domyślny** kursor strzałki umożliwia przełączenie od innych kursorów z powrotem do domyślnego kursora strzałek.|
|Autoprzewijanie|Jeśli masz duży przepływ pracy, możesz chcieć umieścić działanie wykraczające poza widoczne wyświetlanie obszaru powierzchni projektowej. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umożliwia przeciągnięcie działania w kierunku krawędzi powierzchni projektowej najbliższej lokalizacji, w której ma zostać umieszczone działanie. Widok powierzchni projektowej jest automatycznie przewijany w tym kierunku.|
|Tagi inteligentne|Działania, które nie są w pełni skonfigurowane lub nie zostały skonfigurowane prawidłowo, są oznaczone ikoną wykrzyknika. Możesz kliknąć ikonę i wyświetlić listę rozwijaną, które muszą istnieć w działaniu. Następnie można użyć okna **Właściwości** , aby odpowiednio skonfigurować działanie. Gdy wszystkie właściwości są prawidłowe dla działania, ikona wykrzyknika znika.|

## <a name="in-this-section"></a>W tej sekcji
 [Okna przepływów pracy programu Visual Studio (starsza wersja)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Tworzenie starszej wersji projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md)

 [Widoki sekwencyjnego przepływu pracy (starsza wersja)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)

 [Używanie motywów w przepływach pracy (starsza wersja)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Używanie starszej wersji Projektanta przepływu pracy automatu stanów](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Używanie starszej wersji projektanta działań](../workflow-designer/using-the-legacy-activity-designer.md)

 [Starsza wersja projektanta pomocy interfejsu użytkownika programu Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>Zobacz też
 [Opracowywanie przepływów pracy](https://go.microsoft.com/fwlink?LinkID=65010)