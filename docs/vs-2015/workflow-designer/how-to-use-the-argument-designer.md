---
title: 'Instrukcje: Używanie projektanta argumentów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c9ea40a2af8139895a49c993588555f06bfda7f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090709"
---
# <a name="how-to-use-the-argument-designer"></a>Instrukcje: Używanie projektanta argumentów
W porównaniu z poprzednimi wersjami [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], projektanta argumentów ułatwia Zezwalaj na dane przesyłane do i z działania. Projektant jest dostępne po kliknięciu **argumenty** przycisku w lewym dolnym rogu obszaru roboczego projektowania. Projektant zawiera listę argumentów, które są wyświetlane w formie tabelarycznej można sortować według wszystkich nagłówków kolumn, z wyjątkiem **wartość domyślna** kolumny. Każdy argument zawiera nazwę, kierunku w/out/w out/właściwości, typ i domyślne wyrażenie wartości (jeśli istnieje). Nazwa i wartość domyślną wyrażenia są polami tekst do edycji, a typ i kierunek są list rozwijanych. [!INCLUDE[crabout](../includes/crabout-md.md)] argumenty, zobacz [zmienne i argumenty](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).  
  
### <a name="to-create-a-new-argument"></a>Aby utworzyć nowy argument  
  
1. Otwórz rozwiązanie przepływu pracy lub działania w [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. Otwórz projektanta argumentów, klikając pozycję **argumenty** przycisku w lewym dolnym rogu obszaru roboczego projektowania. Pojawi się Projektant argumentów.  
  
3. Kliknij pusty wiersz etykietą **Utwórz Argument**. Spowoduje to dodanie nowego wiersza z argumentem nowe, używając następujących wartości domyślne: argumentx dla **nazwa** gdzie x jest liczbą całkowitą o początkowej wartości 1, który jest automatycznie zwiększany do tworzenia nazw unikatowych argument **w**  dla **kierunek**, i **ciąg** dla **typ argumentu**. Wartość nie jest dodawany do **wartość domyślna**. Wartości te można zmienić w dowolnym momencie podczas procesu projektowania przepływu pracy.  
  
    > [!NOTE]
    >  Aby usunąć argumentu, wybierz argument, klikając go, a następnie naciśnij klawisz **Usuń** klucza.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie projektanta przepływu pracy](../workflow-designer/using-the-workflow-designer.md)   
 [Zmienne i argumenty](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)