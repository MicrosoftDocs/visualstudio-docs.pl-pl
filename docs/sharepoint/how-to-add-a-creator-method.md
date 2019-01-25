---
title: 'Instrukcje: Dodawanie metody Creator | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fe40d6f8b5032dbbffeeda3edaff3b1c89aadb3f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867159"
---
# <a name="how-to-add-a-creator-method"></a>Instrukcje: Dodawanie metody Creator
  Metody Creator dodaje nowe dane do źródła danych jednostki. Usługa łączności danych biznesowych (BDC) wywołuje tę metodę, gdy użytkownicy wybiorą **nowy element** znajdujący się na **wstążki** listy, która jest oparta na modelu. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Aby dodać metody Creator  
  
1. Na **projektanta łączności danych biznesowych**, wybierz jednostkę.  
  
2. Na pasku menu wybierz **widoku** > **Windows inne** >**szczegóły metody BDC**.  
  
    **Szczegóły metody BDC** zostanie otwarte okno. Aby uzyskać więcej informacji na temat tego okna, zobacz [Omówienie narzędzia projektowania modelu usługi łączności danych biznesowych](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. W **Dodaj metodę** wybierz **utworzyć metody Creator**.  
  
    Program Visual Studio dodaje następujące elementy w modelu, a te elementy są wyświetlane w **szczegóły metody BDC** okna.  
  
   - Metodę o nazwie **Utwórz**.  
  
   - Parametr wejściowy metody.  
  
   - Parametr zwracany przez metodę.  
  
   - Deskryptory parametrów typu.  
  
   - Wystąpienia metody dla metody.  
  
     Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. W **Eksploratora rozwiązań**, otwórz menu skrótów pliku kodu usługi, który został wygenerowany dla jednostki, a następnie wybierz **Wyświetl kod**.  
  
    Pliku kodu usługi jednostki zostanie otwarty w edytorze kodu. Aby uzyskać więcej informacji na temat pliku kodu usługi jednostki, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Dodaj kod do metody Creator, który dodaje dane do źródła danych. Poniższy przykład dodaje kontakt do przykładowej bazy danych AdventureWorks programu SQL Server.  
  
   > [!NOTE]  
   >  Zastąp wartość `ServerName` pole z nazwą serwera.  
  
    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Zobacz także
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Instrukcje: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Instrukcje: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Instrukcje: Dodaj parametr do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)  
