---
title: 'Instrukcje: Dodawanie jednostki do modelu | Microsoft Docs'
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b1a7ec1eab5cdcf2e415a4803c51c9da91be29c9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985243"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Instrukcje: Dodawanie jednostki do modelu
  Aby utworzyć jednostkę, Dodaj kontrolkę jednostki z **przybornika** programu Visual Studio do projektanta łączności danych biznesowych (BDC).

### <a name="to-add-an-entity-to-the-model"></a>Aby dodać jednostkę do modelu

1. Utwórz projekt usługi BDC lub Otwórz istniejący projekt usługi BDC. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md).

2. W **przyborniku**, w grupie **BusinessDataCatalog** , Dodaj kontrolkę **Jednostka** do projektanta.

     Nowa jednostka zostanie wyświetlona w projektancie. Program Visual Studio dodaje `<Entity>` element do pliku XML modelu usługi BDC w projekcie. Aby uzyskać więcej informacji na temat atrybutów elementu Entity, zobacz [Entity](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. W projektancie Otwórz menu skrótów dla jednostki, wybierz polecenie **Dodaj**, a następnie wybierz **Identyfikator**.

     Nowy identyfikator zostanie wyświetlony w jednostce.

    > [!NOTE]
    > W oknie **Właściwości** można zmienić nazwę jednostki i identyfikator.

4. Zdefiniuj pola jednostki w klasie. Do projektu można dodać nową klasę lub użyć istniejącej klasy utworzonej przy użyciu innych narzędzi, takich jak Object Relational Designer (Projektant O/R). Poniższy przykład przedstawia klasę jednostki o nazwie Contact.

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md)
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
