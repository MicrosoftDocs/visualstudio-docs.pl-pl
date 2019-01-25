---
title: 'Instrukcje: Dodawanie i usuwanie zależności funkcji | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baedf731a61a13bd6592298e8505dc4a445819e1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871900"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Instrukcje: Dodawanie i usuwanie zależności funkcji
  Z funkcji programu SharePoint może zależeć od innych funkcji dla funkcji lub danych. W takich przypadkach funkcje te można oznaczyć jako zależności dla Twojej funkcji. W ten sposób programu SharePoint server gwarantuje, że funkcje zależne są aktywowane, zanim Twoja funkcja jest aktywowana.  
  
## <a name="add-dependencies"></a>Dodaj zależności  
 Możesz dodać inne funkcje w rozwiązaniu, jako zależności. W ten sposób można upewnij się, że wymagane funkcje są zainstalowane i aktywowane, zanim Twoja funkcja zostanie zainstalowana.  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Aby dodać zależność od funkcji w rozwiązaniu
  
1.  Otwórz projektanta funkcji, rozwiń węzeł **zależności aktywacji funkcji** węzła, a następnie wybierz **Dodaj** przycisku.  
  
2.  W **Dodawanie zależności aktywacji funkcji** okna dialogowego wybierz **dodać zależność od funkcji w rozwiązaniu** przycisk opcji, wybierz tytuł funkcji, która ma zostać dodany jako zależność, a następnie Wybierz **Dodaj** przycisku.  
  
     Można dodać więcej niż jedną funkcję, wybierając tytuły wielu podczas wybierania **Ctrl** klucza.  
  
## <a name="addi-custom-dependencies"></a>Zależności niestandardowej Addi  
 Możesz dodać funkcje, które są już wdrożone na serwerze programu SharePoint jako zależność. W ten sposób sprawdza procesu aktywacji programu SharePoint, upewnij się, że wszystkie funkcje zależne są aktywowane, zanim Twoja funkcja zostanie zainstalowana.  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>Aby dodać zależności według Identyfikatora funkcji
  
1.  Otwórz projektanta funkcji, rozwiń węzeł **zależności aktywacji funkcji** węzła, a następnie wybierz **Dodaj** przycisku.  
  
2.  W **Dodawanie zależności aktywacji funkcji** okna dialogowego wybierz **Dodaj zależność niestandardową** przycisku opcji.  
  
3.  W **identyfikator funkcji** tekstu wprowadź identyfikator GUID dla funkcji, którą chcesz oznaczyć jako zależność aktywacji, a następnie wybierz **Dodaj** przycisku.  
  
## <a name="edit-custom-dependencies"></a>Edytowanie niestandardowej zależności  
 Możesz edytować niestandardowej zależności, które wcześniej dodałeś. Jednak funkcji zależnych, które są w Twoje rozwiązania mogą tylko można usunąć, nie można ich edytować.  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Aby zmienić zależność od funkcji w rozwiązaniu
  
1.  Otwórz projektanta funkcji, a następnie rozwiń **zależności aktywacji funkcji** węzła.  
  
2.  Wybierz nazwę funkcji, którą chcesz edytować, a następnie wybierz **Edytuj** przycisku.  
  
3.  W **Edytuj zależność aktywacji funkcji niestandardowych** okno dialogowe Zmień tytuł, identyfikator funkcji lub opis, a następnie wybierz **przesyłania** przycisku.  
  
## <a name="remove-dependencies"></a>Usuń zależności  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Aby usunąć zależność od funkcji w rozwiązaniu
  
1.  W Projektancie funkcji Rozwiń **zależności aktywacji funkcji** węzła, wybierz nazwę funkcji, którą chcesz usunąć, a następnie wybierz **Usuń** przycisku.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie funkcji SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Instrukcje: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Instrukcje: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
