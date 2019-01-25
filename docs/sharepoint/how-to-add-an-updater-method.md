---
title: 'Instrukcje: Dodawanie metody Updater | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 435674325acdb8b415f0a706f3bca8753d704160
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864166"
---
# <a name="how-to-add-an-updater-method"></a>Instrukcje: Dodawanie metody Updater
  Możesz umożliwić użytkownikom zaktualizować dane biznesowe na liście programu SharePoint zewnętrznych, tworząc *Updater* metody. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Aby utworzyć metody Updater  
  
1. W Projektancie usługi łączności danych biznesowych wybierz jednostkę.  
  
2. Na pasku menu wybierz **widoku** > **Windows inne** > **szczegóły metody BDC**.  
  
    Zostanie otwarte okno Szczegóły metody BDC. Aby uzyskać więcej informacji na temat tego okna, zobacz [Omówienie narzędzia projektowania modelu usługi łączności danych biznesowych](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. W **Dodaj metodę** wybierz **utworzyć metody Updater**.  
  
    Visual Studio dodaje następujące elementy w modelu. Te elementy są wyświetlane w oknie Szczegóły metody BDC.  
  
   - Metoda, która nosi nazwę **aktualizacji**.  
  
   - Parametr wejściowy metody.  
  
   - Deskryptor typu parametru. Visual Studio używa domyślnie do deskryptora typu określonego dla metody wyszukiwania (na przykład: Skontaktuj się z).  
  
   - Wystąpienia metody dla metody.  
  
     Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
   > [!NOTE]  
   >  Jeśli identyfikator typu jednostki reprezentuje pole w tabeli bazy danych, który jest automatycznie generowany, ustaw **pole elementu Pre-Updater** właściwości **True**.  
  
4. W **Eksploratora rozwiązań**, otwórz menu skrótów pliku kodu usługi, który został wygenerowany dla jednostki, a następnie wybierz **Wyświetl kod**.  
  
    Otworzy się w pliku kodu usługi jednostki **Edytor kodu**. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Dodaj kod do metody aktualizacji, aby zaktualizować dane. Poniższy przykład aktualizuje informacje dotyczące kontaktu w przykładowej bazy danych AdventureWorks programu SQL Server.  
  
   > [!NOTE]  
   >  Zastąp wartość `ServerName` pole z nazwą serwera.  
  
    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Zobacz także
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Instrukcje: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Instrukcje: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Instrukcje: Dodaj parametr do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)  
