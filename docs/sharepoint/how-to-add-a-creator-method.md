---
title: 'Instrukcje: Dodawanie metody Creator | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 962e353b5ae82f6dd3eccc2898385fd4b9ee30ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017059"
---
# <a name="how-to-add-a-creator-method"></a>Instrukcje: Dodawanie metody Creator
  Metoda Creator dodaje nowe dane do źródła danych jednostki. Usługa łączności danych biznesowych (BDC) wywołuje tę metodę, gdy użytkownicy wybierają przycisk **nowy element** na **Wstążce** listy, która jest oparta na modelu. Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-add-a-creator-method"></a>Aby dodać metodę Creator

1. W **projektancie BDC**wybierz jednostkę.

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  > **Szczegóły metody BDC**systemu Windows.

    Zostanie otwarte okno **Szczegóły metody BDC** . Aby uzyskać więcej informacji na temat tego okna, zobacz [narzędzia projektowania modelu usługi BDC — Omówienie](../sharepoint/bdc-model-design-tools-overview.md).

3. Z listy **Dodaj metodę** wybierz polecenie **Utwórz twórcę metody**.

    Program Visual Studio dodaje do modelu następujące elementy, które są wyświetlane w oknie **Szczegóły metody BDC** .

   - Metoda o nazwie **Create**.

   - Parametr wejściowy dla metody.

   - Parametr Return dla metody.

   - Deskryptory typu dla parametrów.

   - Wystąpienie metody dla metody.

     Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

4. W **Eksplorator rozwiązań**Otwórz menu skrótów pliku kodu usługi, który został wygenerowany dla jednostki, a następnie wybierz polecenie **Wyświetl kod**.

    Plik kodu usługi jednostki zostanie otwarty w edytorze kodu. Aby uzyskać więcej informacji na temat pliku kodu usługi jednostki, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Dodaj kod do metody Creator, która dodaje dane do źródła danych. Poniższy przykład dodaje kontakt do przykładowej bazy danych AdventureWorks dla SQL Server.

   > [!NOTE]
   > Zamień wartość `ServerName` pola na nazwę serwera.

    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]

## <a name="see-also"></a>Zobacz też
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md)
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
