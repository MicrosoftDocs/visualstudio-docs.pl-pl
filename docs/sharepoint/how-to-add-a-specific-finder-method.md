---
title: 'Instrukcje: Dodawanie określonej metody wyszukiwania | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6f52caf33820b230eb00b1be2999fe7f972176f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615289"
---
# <a name="how-to-add-a-specific-finder-method"></a>Instrukcje: Dodawanie określonej metody wyszukiwania
  Może zwrócić wystąpienia pojedynczej jednostki, tworząc *określonej metody wyszukiwania* metody. Usługa łączności danych biznesowych (BDC) wykonuje konkretną metodę wyszukiwania, gdy użytkownik wybierze jednostki w części sieci web danych biznesowych lub listy zewnętrznej. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Aby utworzyć określonej metody wyszukiwania

1. Na **projektanta łączności danych biznesowych**, wybierz jednostkę.

    Aby uzyskać informacje dotyczące sposobu dodawania jednostki do **projektanta łączności danych biznesowych** w programie Visual Studio, zobacz [jak: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Na pasku menu wybierz **widoku** > **Windows inne**, **szczegóły metody BDC**.

    **Szczegóły metody BDC** zostanie otwarte okno. Aby uzyskać więcej informacji na temat tego okna, zobacz [Omówienie narzędzia projektowania modelu usługi łączności danych biznesowych](../sharepoint/bdc-model-design-tools-overview.md).

3. W **Dodaj metodę** wybierz **Tworzenie określonej metody wyszukiwania**.

    Visual Studio dodaje następujące elementy w modelu. Te elementy są wyświetlane w **szczegóły metody BDC** okna.

   - Metoda.

   - Parametr wejściowy metody.

   - Parametr zwracany przez metodę.

   - Deskryptor typu dla każdego parametru.

   - Wystąpienia metody dla metody.

     Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Otwórz program Visual Studio **właściwości** okna.

5. Deskryptor typu parametru zwracanego należy skonfigurować jako deskryptora typu. Aby uzyskać informacje o sposobach tworzenia deskryptora typu, zobacz [jak: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   >  Nie trzeba wykonać ten krok, jeśli metoda wyszukiwania zostały dodane do jednostki. Visual Studio używa deskryptora typu, który zostały zdefiniowane w metodę wyszukiwania.

   > [!NOTE]
   >  Jeśli pole identyfikatora typu jednostki reprezentuje pole w tabeli bazy danych, która jest generowana automatycznie, ustaw **tylko do odczytu** właściwości pola Identyfikator **True**.

6. W **szczegóły metody** okna, wybierz wystąpienie metody metody.

7. W **okno właściwości**ustaw **zwraca nazwę parametru** właściwość na nazwę parametru zwracanego metody. Aby uzyskać więcej informacji na temat właściwości wystąpienia metody zobacz [elementu MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).

8. W **Eksploratora rozwiązań**, otwórz menu skrótów pliku kodu usługi, który został wygenerowany dla jednostki, a następnie wybierz **Wyświetl kod**.

    Pliku kodu usługi jednostki zostanie otwarty w edytorze kodu. Aby uzyskać więcej informacji na temat pliku kodu usługi jednostki, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Dodaj kod do metody wyszukiwania. Kod będzie wykonywał następujące zadania:

   - Pobiera rekord ze źródła danych.

   - Zwraca jednostkę usługi łączności danych biznesowych.

     Poniższy przykład zwraca kontakt z przykładowej bazy danych AdventureWorks programu SQL Server.

     > [!NOTE]
     >  Zastąp wartość `ServerName` pole z nazwą serwera.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>Zobacz także
- [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Instrukcje: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodaj parametr do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
