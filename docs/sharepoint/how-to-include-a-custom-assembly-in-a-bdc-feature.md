---
title: 'Instrukcje: Dołączanie niestandardowego zestawu w funkcji BDC | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6de3313dad06c009244a8b784e81bf7d2a768c3b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443112"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Instrukcje: Dołączanie niestandardowego zestawu w funkcji BDC
  Projekt można odwołuje się do zestawów z innych projektów w tym samym rozwiązaniu. Jednakże, należy dodać te zestawy do pliku funkcji projektu, przy użyciu **Przypisz przywoływane zestawy do elementów LobSystem** okno dialogowe.

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Aby Dołączanie niestandardowego zestawu w funkcji (BDC) łączności danych biznesowych

1. W **Eksploratora rozwiązań**, wybierz folder, który zawiera model usługi łączności danych biznesowych.

2. Na **widoku** menu, kliknij przycisk **okno właściwości**.

3. W **właściwości** oknie Wybierz **zestawy** właściwości, a następnie przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "przenośnych ASP.NET Projektant elipsy")).

     **Przypisz przywoływane zestawy do elementów LobSystem** pojawi się okno dialogowe.

4. W **wybierz zestaw** wybierz zestaw niestandardowy.

    > [!NOTE]
    > Zestawy są wyświetlane tylko w **Przypisz przywoływane zestawy do elementów LobSystem** okno dialogowe, jeśli zostały dodane odwołanie do projektu, który zawiera zestaw. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

5. W **właściwości odwołania** grupy, Otwórz listę, która pojawia się dla **zakres elementu LobSystem** właściwość, należy wybrać System LOB metod, które zestaw niestandardowy, a następnie wybierz **OK**  przycisku.

    > [!NOTE]
    > Aby debugować kod w zestaw niestandardowy, należy dodać zestaw do pakietu rozwiązań. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie zestawów dodatkowych](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Instrukcje: Dodawanie istniejącego modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Instrukcje: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Integragte danych biznesowych w programie SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
