---
title: 'Instrukcje: Dodawanie metody Aktualizator | Microsoft Docs'
description: Dowiedz się, jak umożliwić użytkownikom aktualizowanie danych firmowych na liście zewnętrznej programu SharePoint przez dodanie metody Aktualizator.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fff7083305d4e19495b81525c8a67a42c5ff6c70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967504"
---
# <a name="how-to-add-an-updater-method"></a>Instrukcje: Dodawanie metody Aktualizator
  Można umożliwić użytkownikom aktualizowanie danych firmowych na liście zewnętrznej programu SharePoint, tworząc metodę *Aktualizator* . Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Aby utworzyć metodę Aktualizator

1. W projektancie BDC wybierz jednostkę.

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  >  **Szczegóły metody BDC** systemu Windows.

    Zostanie otwarte okno Szczegóły metody BDC. Aby uzyskać więcej informacji na temat tego okna, zobacz [narzędzia projektowania modelu usługi BDC — Omówienie](../sharepoint/bdc-model-design-tools-overview.md).

3. Z listy **Dodaj metodę** wybierz pozycję **Utwórz metodę Aktualizator**.

    Program Visual Studio dodaje do modelu następujące elementy. Te elementy pojawiają się w oknie Szczegóły metody BDC.

   - Metoda o nazwie **Update**.

   - Parametr wejściowy dla metody.

   - Deskryptor typu dla parametru. Domyślnie program Visual Studio używa deskryptora typu jednostki, który został zdefiniowany dla metody wyszukiwania (na przykład: contact).

   - Wystąpienie metody dla metody.

     Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Jeśli identyfikator typu jednostki reprezentuje pole w tabeli bazy danych, które nie jest generowane automatycznie, ustaw właściwość **Aktualizator pola** na **wartość true**.

4. W **Eksplorator rozwiązań** Otwórz menu skrótów pliku kodu usługi, który został wygenerowany dla jednostki, a następnie wybierz polecenie **Wyświetl kod**.

    Plik kodu usługi jednostki zostanie otwarty w **edytorze kodu**. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Dodaj kod do metody Update, aby zaktualizować dane. Poniższy przykład aktualizuje informacje o kontakcie w przykładowej bazie danych AdventureWorks dla SQL Server.

   > [!NOTE]
   > Zamień wartość `ServerName` pola na nazwę serwera.

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>Zobacz też
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)
- [Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md)
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
