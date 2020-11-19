---
title: 'Instrukcje: uwzględnianie niestandardowego zestawu w funkcji BDC | Microsoft Docs'
description: Dołącz zestawy niestandardowe do funkcji łączności danych biznesowych (BDC), dzięki czemu projekt może odwoływać się do zestawów z innych projektów w tym samym rozwiązaniu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: e7a2a0109faca4da5406b45b4d606ae8a5cd0685
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903471"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Instrukcje: uwzględnianie niestandardowego zestawu w funkcji BDC
  Projekt może odwoływać się do zestawów z innych projektów w tym samym rozwiązaniu. Należy jednak dodać te zestawy do pliku funkcji projektu za pomocą okna dialogowego **Przypisz przywoływane zestawy do LobSystems** .

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Aby dołączyć zestaw niestandardowy do funkcji łączności danych biznesowych (BDC)

1. W **Eksplorator rozwiązań** wybierz folder zawierający model usługi BDC.

2. W menu **Widok** kliknij **okno właściwości**.

3. W oknie **Właściwości** wybierz właściwość **zestawy** , a następnie przycisk wielokropka (![ASP.net Mobile Designer — Elipsa](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")).

     Zostanie wyświetlone okno dialogowe **przypisywanie przywoływanych zestawów do LobSystems** .

4. Z listy **Wybierz zestaw** wybierz zestaw niestandardowy.

    > [!NOTE]
    > Zestawy pojawiają się tylko w oknie dialogowym **przypisywanie przywoływanych zestawów do LobSystems** , jeśli dodano odwołanie do projektu, który zawiera zestaw. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie odwołań za pomocą okna dialogowego Dodawanie odwołania](/previous-versions/wkze6zky(v=vs.140)).

5. W grupie **właściwości odwołania** Otwórz listę, która pojawia się dla właściwości **Zakres klasy LobSystem** , wybierz System LOB metod, które używają zestawu niestandardowego, a następnie wybierz przycisk **OK** .

    > [!NOTE]
    > Aby debugować kod w zestawie niestandardowym, należy dodać zestaw do pakietu rozwiązania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie dodatkowych zestawów](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Instrukcje: Dodawanie istniejącego pliku modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Tworzenie modelu łączności danych firmy](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Instrukcje: Tworzenie modelu usługi BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Integragte dane biznesowe w programie SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)