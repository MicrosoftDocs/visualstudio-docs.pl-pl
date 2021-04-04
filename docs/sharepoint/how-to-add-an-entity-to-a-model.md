---
title: 'Instrukcje: Dodawanie jednostki do modelu | Microsoft Docs'
description: Dodaj jednostkę do modelu, dodając kontrolkę jednostki z przybornika programu Visual Studio do projektanta łączności danych biznesowych (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94d34e6a623438cd0e2d63d74ee2321841a0582a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216777"
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

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs" id="Snippet1":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb" id="Snippet1":::

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md)
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
