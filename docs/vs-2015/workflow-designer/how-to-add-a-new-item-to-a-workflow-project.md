---
title: 'Instrukcje: Dodawanie nowego elementu do projektu przepływu pracy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656633"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Instrukcje: Dodawanie nowego elementu do projektu przepływu pracy
Po utworzeniu projektu przepływu pracy można dodać do projektu działania przepływu pracy, projektanci i inne znane elementy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 W poniższej tabeli wymieniono elementy [!INCLUDE[wf](../includes/wf-md.md)], które można dodać do projektu przepływu pracy.

|Nazwa|Opis|
|----------|-----------------|
|Działanie|Działanie składające się z innych działań. Wybranie tego elementu powoduje dodanie tego samego pliku XAML do projektu, jak uzyskano podczas wybierania szablonu **biblioteki działań** dla nowego projektu. [!INCLUDE[crabout](../includes/crabout-md.md)] tej procedury, zobacz [How to: Create a Activity Library](../workflow-designer/how-to-create-an-activity-library.md).|
|Projektant działań|Projektant umożliwiający dostosowanie środowiska czasu projektowania działania. Wybranie tego elementu powoduje dodanie do projektu tych samych plików jak w przypadku wybrania szablonu **biblioteki projektanta działań** dla nowego projektu. [!INCLUDE[crabout](../includes/crabout-md.md)] tej procedury, zobacz [How to: Create a Projektant działań Library](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Działanie kodu|Działanie z logiką wykonywania zapisaną w kodzie. Plik kodu źródłowego z przesłonięciem metody <xref:System.Activities.CodeActivity.Execute%2A> jest już wygenerowany dla Ciebie.|
|Usługa przepływu pracy WCF|Usługa [!INCLUDE[indigo2](../includes/indigo2-md.md)] utworzona przy użyciu działań przepływu pracy. Wybranie tego elementu powoduje dodanie do projektu tych samych plików, co podczas wybierania szablonu **aplikacji usługi przepływu pracy WCF** dla nowego projektu. [!INCLUDE[crabout](../includes/crabout-md.md)] tej procedury, zobacz [jak: Tworzenie aplikacji usługi przepływu pracy WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Aby dodać nowy element do projektu przepływu pracy

1. W menu **projekt** kliknij polecenie **Dodaj nowy element.** ...

     Zostanie otwarte okno dialogowe **Dodaj nowy element** .

2. W okienku **zainstalowane szablony** wybierz pozycję Grupa **przepływu pracy** .

3. Wybierz jeden z czterech elementów. W poprzedniej tabeli wymieniono dostępne opcje.

4. Wpisz odpowiednią nazwę dla elementu w polu **Nazwa** w dolnej części okna dialogowego.

5. Kliknij przycisk **Dodaj** , aby dodać element do bieżącego projektu przepływu pracy.

## <a name="see-also"></a>Zobacz też
 [Tworzenie projektu przepływu pracy](../workflow-designer/creating-a-workflow-project.md)