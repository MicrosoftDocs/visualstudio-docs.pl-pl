---
title: 'Instrukcje: dodawanie określonej metody wyszukiwania | Microsoft Docs'
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
ms.openlocfilehash: 732921b021d7887faf31dd3f602f5400c1d06a59
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985263"
---
# <a name="how-to-add-a-specific-finder-method"></a>Instrukcje: dodawanie określonej metody wyszukiwania
  Wystąpienie pojedynczej jednostki można zwrócić, tworząc określoną metodę *wyszukiwania* . Usługa łączności danych biznesowych (BDC) wykonuje określoną metodę wyszukiwania, gdy użytkownik wybierze jednostkę w składniku Web Part danych biznesowych lub liście zewnętrznej. Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Aby utworzyć konkretną metodę wyszukiwania

1. W **projektancie BDC**wybierz jednostkę.

    Aby uzyskać informacje na temat dodawania jednostki do **projektanta usługi BDC** w programie Visual Studio, zobacz [How to: Add a Entity to a model](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Na pasku menu wybierz **widok** > **inne okna**, **Szczegóły metody BDC**.

    Zostanie otwarte okno **Szczegóły metody BDC** . Aby uzyskać więcej informacji na temat tego okna, zobacz [narzędzia projektowania modelu usługi BDC — Omówienie](../sharepoint/bdc-model-design-tools-overview.md).

3. Z listy **Dodaj metodę** wybierz opcję **Utwórz konkretną metodę wyszukiwania**.

    Program Visual Studio dodaje do modelu następujące elementy. Te elementy pojawiają się w oknie **Szczegóły metody BDC** .

   - Metoda.

   - Parametr wejściowy dla metody.

   - Parametr Return dla metody.

   - Deskryptor typu dla każdego parametru.

   - Wystąpienie metody dla metody.

     Aby uzyskać więcej informacji, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Otwórz okno **Właściwości** programu Visual Studio.

5. Skonfiguruj deskryptor typu dla parametru Return jako deskryptora typu jednostki. Informacje o sposobach tworzenia deskryptora typu jednostki znajdują się w temacie [How to: define The Type Descriptor of an Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Nie trzeba wykonywać tego kroku, jeśli dodano metodę wyszukiwania do jednostki. Program Visual Studio używa deskryptora typu zdefiniowanego w metodzie wyszukiwania.

   > [!NOTE]
   > Jeśli pole identyfikatora typu jednostki reprezentuje pole w tabeli bazy danych, która jest generowana automatycznie, ustaw właściwość tylko do **odczytu** pola Identyfikator na **wartość true**.

6. W oknie **Szczegóły metody** wybierz wystąpienie metody metody.

7. W **oknie właściwości**ustaw właściwość **Nazwa parametru powrotu** na nazwę parametru powrotu metody. Aby uzyskać więcej informacji na temat właściwości wystąpienia metody, zobacz element [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. W **Eksplorator rozwiązań**Otwórz menu skrótów pliku kodu usługi, który został wygenerowany dla jednostki, a następnie wybierz polecenie **Wyświetl kod**.

    Plik kodu usługi jednostki zostanie otwarty w edytorze kodu. Aby uzyskać więcej informacji na temat pliku kodu usługi jednostki, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Dodaj kod do określonej metody wyszukiwania. Kod będzie wykonywał następujące zadania:

   - Pobiera rekord ze źródła danych.

   - Zwraca jednostkę do usługi BDC.

     Poniższy przykład zwraca kontakt z przykładowej bazy danych AdventureWorks dla SQL Server.

     > [!NOTE]
     > Zastąp wartość pola `ServerName` nazwą serwera.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>Zobacz także
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md)
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
