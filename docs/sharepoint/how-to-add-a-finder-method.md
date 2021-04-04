---
title: 'Instrukcje: Dodawanie metody wyszukiwania | Microsoft Docs'
description: Dodaj metodę wyszukiwania w programie Visual Studio, która umożliwia usłudze łączności danych biznesowych (BDC) wyświetlanie listy jednostek w składniku Web Part lub liście programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6bd75c94e2f0f557b85d945d141f952950abb2eb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216348"
---
# <a name="how-to-add-a-finder-method"></a>Instrukcje: Dodawanie metody wyszukiwania
  Aby włączyć usługę łączności danych biznesowych (BDC) do wyświetlania listy jednostek w składniku Web Part lub liście, należy utworzyć metodę *wyszukiwania* . Metoda wyszukiwania to specjalna metoda zwracająca kolekcję wystąpień jednostek. Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Aby utworzyć metodę wyszukiwania

1. W **projektancie BDC** wybierz jednostkę.

    Aby uzyskać więcej informacji, zobacz [jak: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  >  **Szczegóły metody BDC** systemu Windows.

    Zostanie otwarte okno **Szczegóły metody BDC** . Aby uzyskać więcej informacji na temat okna **Szczegóły metody BDC** , zobacz [Omówienie narzędzi projektowania modelu usługi BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Na liście **Dodaj metodę** wybierz pozycję **Utwórz metodę wyszukiwania**.

    Program Visual Studio dodaje metodę, parametr Return i deskryptor typu.

4. Skonfiguruj deskryptor typu jako deskryptor typu kolekcji jednostek. Aby uzyskać więcej informacji na temat sposobu tworzenia deskryptora typu kolekcji jednostek, zobacz [How to: define The Type Descriptor of an Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Nie trzeba wykonywać tego kroku, jeśli dodano określoną metodę wyszukiwania do jednostki. Program Visual Studio używa deskryptora typu zdefiniowanego w określonej metodzie wyszukiwania.

5. W **Eksplorator rozwiązań** Otwórz menu skrótów pliku kodu usługi, który został wygenerowany dla jednostki, a następnie wybierz polecenie **Wyświetl kod**. Aby uzyskać więcej informacji na temat pliku kodu usługi, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Dodaj kod do metody wyszukiwania. Ten kod wykonuje następujące zadania:

   - Pobiera dane ze źródła danych.

   - Zwraca listę jednostek do usługi BDC.

     Poniższy przykład zwraca kolekcję `Contact` jednostek przy użyciu danych z przykładowej bazy danych AdventureWorks dla SQL Server.

   > [!NOTE]
   > Zamień wartość `ServerName` pola na nazwę serwera.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet2":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet2":::

## <a name="see-also"></a>Zobacz też
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md)
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)
- [Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
