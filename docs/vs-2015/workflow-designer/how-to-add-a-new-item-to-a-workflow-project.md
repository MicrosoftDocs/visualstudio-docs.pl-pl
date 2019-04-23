---
title: 'Instrukcje: Dodaj nowy element do projektu przepływu pracy | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ecc310896f7b938025d42e06ac5ef0ec8bac3d35
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063632"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Instrukcje: Dodawanie nowego elementu do projektu przepływu pracy
Po utworzeniu projektu przepływu pracy, można dodać działania przepływu pracy, projektantów i innych znanych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] elementy do projektu.  
  
 W poniższej tabeli wymieniono [!INCLUDE[wf](../includes/wf-md.md)] elementy, które można dodać do projektu przepływu pracy.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|Działanie|Działanie składa się z innymi działaniami. Wybranie tej pozycji dodaje ten sam plik XAML do projektu, jak można uzyskać po wybraniu **Biblioteka działań** szablonu dla nowego projektu. [!INCLUDE[crabout](../includes/crabout-md.md)] Korzystając z tej procedury zobacz [jak: Tworzenie biblioteki działań](../workflow-designer/how-to-create-an-activity-library.md).|  
|Projektant działań|Projektant umożliwiający dostosowanie środowiska czasu projektowania, działania. Wybranie tej pozycji dodaje te same pliki do projektu, jak można uzyskać po wybraniu **Biblioteka projektanta działań** szablonu dla nowego projektu. [!INCLUDE[crabout](../includes/crabout-md.md)] Korzystając z tej procedury zobacz [jak: Tworzenie biblioteki projektanta działań](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Działanie kodu|Działanie z logiką wykonywania zapisaną w kodzie. Plik kodu źródłowego za pomocą zastąpienia z <xref:System.Activities.CodeActivity.Execute%2A> metoda została już wygenerowana dla Ciebie.|  
|Usługa przepływu pracy WCF|A [!INCLUDE[indigo2](../includes/indigo2-md.md)] oferująca przy użyciu działań przepływu pracy. Wybranie tej pozycji dodaje te same pliki do projektu, jak można uzyskać po wybraniu **aplikacja usługi przepływu pracy WCF** szablonu dla nowego projektu. [!INCLUDE[crabout](../includes/crabout-md.md)] Korzystając z tej procedury zobacz [jak: Tworzenie aplikacji usługi przepływu pracy WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>Aby dodać nowy element do projektu przepływu pracy  
  
1. Na **projektu** menu, kliknij przycisk **Dodaj nowy element...** .  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2. W **zainstalowane szablony** okienku wybierz **przepływu pracy** grupy.  
  
3. Wybierz jedną z czterech elementów. W poprzedniej tabeli wymieniono opcje dostępne do wyboru.  
  
4. Wpisz odpowiednią nazwę dla elementu w **nazwa** u dołu okna dialogowego.  
  
5. Kliknij przycisk **Dodaj** Aby dodać element do bieżącego projektu przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)