---
title: 'Instrukcje: Dodawanie metody wyszukiwania | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dc61db134063c1e300a2620f611d62497fffe6e1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608074"
---
# <a name="how-to-add-a-finder-method"></a>Instrukcje: Dodawanie metody wyszukiwania
  Aby włączyć usługi łączności danych biznesowych (BDC) wyświetlić listę jednostek w części sieci web lub na liście, należy utworzyć *wyszukiwania* metody. Metoda wyszukiwania jest specjalne metody, które zwraca kolekcję wystąpień jednostek. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Aby utworzyć metodę wyszukiwania

1. Na **projektanta łączności danych biznesowych**, wybierz jednostkę.

    Aby uzyskać więcej informacji, zobacz [jak: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Na pasku menu wybierz **widoku** > **Windows inne** > **szczegóły metody BDC**.

    **Szczegóły metody BDC** zostanie otwarte okno. Aby uzyskać więcej informacji na temat **szczegóły metody BDC** okna, zobacz [Omówienie narzędzia projektowania modelu usługi łączności danych biznesowych](../sharepoint/bdc-model-design-tools-overview.md).

3. W **Dodaj metodę** wybierz **Utwórz metodę wyszukującą**.

    Visual Studio dodaje metodę, parametr zwracany i deskryptor typu.

4. Skonfiguruj deskryptor typu jako deskryptora typu kolekcji. Aby uzyskać więcej informacji o sposobach tworzenia deskryptora typu kolekcji, zobacz [jak: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   >  Nie trzeba wykonać ten krok, jeśli określonej metody wyszukiwania zostały dodane do jednostki. Visual Studio używa deskryptora typu, który zostały zdefiniowane w określonej metody wyszukiwania.

5. W **Eksploratora rozwiązań**, otwórz menu skrótów pliku kodu usługi, który został wygenerowany dla jednostki, a następnie wybierz **Wyświetl kod**. Aby uzyskać więcej informacji na temat pliku kodu usługi, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Dodaj kod do metody wyszukiwania. Kod będzie wykonywał następujące zadania:

   - Pobiera dane ze źródła danych.

   - Zwraca listę jednostek do usługi łączności danych biznesowych.

     Poniższy przykład zwraca kolekcję `Contact` jednostek przy użyciu danych z przykładowej bazy danych AdventureWorks programu SQL Server.

   > [!NOTE]
   >  Zastąp wartość `ServerName` pole z nazwą serwera.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>Zobacz także
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Instrukcje: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Instrukcje: Dodaj parametr do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
