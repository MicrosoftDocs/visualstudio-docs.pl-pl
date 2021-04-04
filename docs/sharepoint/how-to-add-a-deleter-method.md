---
title: 'Instrukcje: Dodawanie metody usuwania | Microsoft Docs'
description: Dowiedz się, jak dodać metodę usuwania w Projektancie usługi BDC programu Visual Studio, aby użytkownik końcowy mógł usunąć rekord danych z listy zewnętrznej w witrynie programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f5c9dc0a5ca6b7651b4ddc1f4b58a8b72305a1a5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217999"
---
# <a name="how-to-add-a-deleter-method"></a>Instrukcje: Dodawanie metody usuwania
  Można umożliwić użytkownikowi końcowemu usunięcie rekordu danych z listy zewnętrznej w witrynie programu SharePoint, dodając metodę usuwania do modelu. Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>Aby utworzyć metodę usuwania

1. W **projektancie BDC** wybierz jednostkę.

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  >  **Szczegóły metody BDC** systemu Windows.

    Zostanie otwarte okno **Szczegóły metody BDC** . Aby uzyskać więcej informacji na temat tego okna, zobacz [narzędzia projektowania modelu usługi BDC — Omówienie](../sharepoint/bdc-model-design-tools-overview.md).

3. Z listy **Dodaj metodę** wybierz pozycję **Utwórz metodę usuwania**.

    Program Visual Studio dodaje do modelu następujące elementy. Te elementy pojawiają się w oknie **Szczegóły metody BDC** .

   - Metoda o nazwie **delete**.

   - Parametr wejściowy dla metody.

   - Deskryptor typu dla parametru.

   - Wystąpienie metody dla metody.

     Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

4. W **Eksplorator rozwiązań** Otwórz menu skrótów pliku kodu usługi, który został wygenerowany dla jednostki, a następnie wybierz polecenie **Wyświetl kod**.

    Plik kodu usługi jednostki zostanie otwarty w edytorze kodu. Aby uzyskać więcej informacji na temat pliku kodu usługi jednostki, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Dodaj kod do metody Delete, aby usunąć rekord. Poniższy przykład usuwa element wiersza z zamówienia sprzedaży przy użyciu przykładowej bazy danych AdventureWorks dla SQL Server.

   > [!NOTE]
   > Metoda w tym przykładzie używa dwóch parametrów wejściowych.

   > [!NOTE]
   > Zamień wartość `ServerName` pola na nazwę serwera.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet6":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet6":::

## <a name="see-also"></a>Zobacz też
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
