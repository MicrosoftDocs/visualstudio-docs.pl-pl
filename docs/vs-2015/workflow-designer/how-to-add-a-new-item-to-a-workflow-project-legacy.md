---
title: 'Instrukcje: Dodawanie nowego elementu do projektu przepływu pracy (starsza wersja) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46f6e9daafc2688b9bea75cba9eddd8c8a53c9bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656670"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Instrukcje: Dodawanie nowego elementu do projektu przepływu pracy (starsza wersja)
Po utworzeniu projektu przepływu pracy przy użyciu starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] dostarczonej przez [!INCLUDE[vs2010](../includes/vs2010-md.md)] program [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] , można dodać [!INCLUDE[wf](../includes/wf-md.md)] elementy i inne znane [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] elementy do projektu.

 W poniższej tabeli wymieniono [!INCLUDE[wf2](../includes/wf2-md.md)] elementy, które można dodać do projektu przepływu pracy.

|Element|Opis|
|----------|-----------------|
|Działanie|Działanie z definicją działania w pliku kodu projektanta i kodem użytkownika w osobnym pliku kodu.|
|Działanie (z separacją kodu)|Definicja działania wyrażona jako znacznik przepływu pracy i kod użytkownika w osobnym pliku kodu.|
|Sekwencyjny przepływ pracy (kod)|Sekwencyjny przepływ pracy z definicją przepływu pracy w pliku kodu projektanta i kodem użytkownika w osobnym pliku kodu.|
|Sekwencyjny przepływ pracy (z separacją kodu)|Sekwencyjny przepływ pracy z definicją przepływu pracy wyrażoną jako znacznik przepływu i kod użytkownika w osobnym pliku kodu.|
|Przepływ pracy automatu Stanów (kod)|Przepływ pracy automatu Stanów z definicją przepływu pracy w pliku kodu projektanta i kodem użytkownika w osobnym pliku kodu.|
|Przepływ pracy automatu Stanów (z separacją kodu)|Przepływ pracy automatu Stanów z definicją przepływu pracy wyrażoną w postaci znaczników i kodu użytkownika w osobnym pliku kodu.|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Aby dodać nowy element do projektu przepływu pracy

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

     Zostanie otwarte okno dialogowe **Dodaj nowy element** .

2. Wybierz element.

     W poprzedniej tabeli wymieniono dostępne Windows Workflow Foundation wyboru.

3. Kliknij przycisk **Dodaj** , aby dodać element do projektu przepływu pracy.

## <a name="see-also"></a>Zobacz też
 [Tworzenie starszej wersji projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md)