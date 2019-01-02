---
title: 'Instrukcje: Dodawanie jednostki do modelu | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 347728ac4f096359f06ca7823adfcd1b25ff527a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964037"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Instrukcje: Dodawanie jednostki do modelu
  Aby utworzyć jednostki, należy dodać kontrolkę typu jednostki z programu Visual Studio **przybornika** do projektanta łączności danych biznesowych (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Aby dodać obiekt do modelu  
  
1.  Tworzenie projektu usługi łączności danych biznesowych lub Otwórz istniejący projekt usługi łączności danych biznesowych. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  W **przybornika**, z **BusinessDataCatalog** grupy, Dodaj **jednostki** formant do projektanta.  
  
     Nowa jednostka zostanie wyświetlony w projektancie. Program Visual Studio dodaje `<Entity>` elementu XML modelu BDC w projekcie. Aby uzyskać więcej informacji na temat atrybutów elementu jednostki zobacz [jednostki](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  W projektancie, otwórz menu skrótów dla jednostki, wybierz polecenie **Dodaj**, a następnie wybierz **identyfikator**.  
  
     Nowy identyfikator pojawia się w jednostce.  
  
    > [!NOTE]  
    >  Możesz zmienić nazwę jednostki i identyfikatora w **właściwości** okna.  
  
4.  Definiowanie pól jednostki w klasie. Możesz dodać nową klasę do projektu lub użyj istniejącej klasy utworzone przy użyciu innych narzędzi, takich jak Object Relational Designer (O/R Designer). Poniższy przykład przedstawia klasę jednostki o nazwie kontaktu.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Instrukcje: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Instrukcje: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)  
