---
title: 'Instrukcje: Tworzenie modelu usługi BDC | Microsoft Docs'
description: Utwórz model łączności danych biznesowych (BDC) przy użyciu szablonu programu Visual Studio dla tego rodzaju elementu, a następnie Dodaj model do dowolnego projektu programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f95533a5ad3955ee00829194bc4da1498baace0
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850679"
---
# <a name="how-to-create-a-bdc-model"></a>Instrukcje: Tworzenie modelu usługi BDC
  Model łączności danych biznesowych (BDC) można utworzyć za pomocą szablonu dla tego rodzaju elementu, a następnie dodać model do dowolnego projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md). Aby uzyskać więcej informacji na temat projektowania modelu, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-bdc-project"></a>Aby utworzyć projekt usługi BDC

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

    > [!NOTE]
    > Jeśli środowisko IDE jest skonfigurowane do korzystania z ustawień tworzenia Visual Basic, wybierz pozycję **plik**  >  **Nowy projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

2. W obszarze **Visual Basic** lub **Visual C#** wybierz pozycję **Office/SharePoint**, **rozwiązania programu SharePoint**.

3. W okienku **Szablony** wybierz element **SharePoint 2013-pusty projekt** , a następnie wybierz przycisk **OK** .

     Zostanie otwarty **Kreator dostosowania programu SharePoint** .

4. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** Określ adres URL witryny programu SharePoint na komputerze lokalnym, wybierz przycisk opcji **Wdróż jako farmę** , a następnie wybierz przycisk **Zakończ** .

     Będziesz testować model w określonej witrynie programu SharePoint.

    > [!IMPORTANT]
    > Należy wdrożyć projekt jako rozwiązanie farmy, ponieważ modele usługi BDC obsługują tylko rozwiązania farmy.

     Zostanie utworzony pusty projekt programu SharePoint.

5. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

6. W oknie dialogowym **Dodaj nowy element** wybierz węzeł **Office/SharePoint** .

7. Na liście szablonów programu SharePoint wybierz pozycję **model łączności danych firmowych (tylko rozwiązanie farmy)**.

8. W polu **Nazwa** Określ nazwę modelu usługi BDC, a następnie wybierz przycisk **Dodaj** .

     Element **modelu łączności danych firmowych** jest dodawany do projektu. Domyślnie model jest wyświetlany w Projektancie usługi BDC. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych firmowych](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Zobacz także
- [Tworzenie modelu łączności danych firmy](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Instrukcje: Dodawanie istniejącego pliku modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Instrukcje: korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Instrukcje: uwzględnianie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
