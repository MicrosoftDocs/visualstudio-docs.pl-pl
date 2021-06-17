---
title: 'How to: Create a BDC Model | (Tworzyć model BDC) Microsoft Docs'
description: Utwórz model łączności danych biznesowych (BDC) przy użyciu szablonu Visual Studio dla tego rodzaju elementu, a następnie dodaj model do dowolnego projektu programu SharePoint.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd5184f87cf3895e1519a91e6f7e6661702f1181
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112414"
---
# <a name="how-to-create-a-bdc-model"></a>How to: Create a BDC model (Tworzyć model BDC)

  Model łączności danych biznesowych (BDC, Business Data Connectivity) można utworzyć przy użyciu szablonu dla tego rodzaju elementu, a następnie dodać model do dowolnego projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [Create a business data connectivity model (Tworzenie modelu łączności danych biznesowych).](../sharepoint/creating-a-business-data-connectivity-model.md) Aby uzyskać więcej informacji na temat sposobu projektowania modelu, zobacz Design a business data connectivity model (Projektowanie [modelu łączności danych biznesowych).](../sharepoint/designing-a-business-data-connectivity-model.md)

## <a name="to-create-a-bdc-project"></a>Aby utworzyć projekt BDC

1. Na pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).**
::: moniker range="=vs-2017"
   > [!NOTE]
   > Jeśli twoje idee są ustawione do używania Visual Basic dewelopera, wybierz pozycję File New Project **(Plik**  >  **nowy projekt).**

  Zostanie **otwarte okno dialogowe** Nowy projekt.

2. W obszarze **Visual Basic** **lub Visual C#** wybierz **pozycję Office/SharePoint,** **SharePoint Solutions.**

3. W **okienku** Szablony wybierz element **SharePoint 2013 — Pusty** projekt, a następnie wybierz **przycisk OK.**

     Zostanie **otwarty Kreator dostosowywania programu SharePoint.**
::: moniker-end
::: moniker range=">=vs-2019"
2. W **oknie dialogowym Tworzenie nowego projektu** wybierz pusty projekt programu *SharePoint** dla określonej zainstalowanej wersji programu SharePoint. Jeśli na przykład masz zainstalowany program SharePoint 2019, wybierz szablon **SharePoint 2019 — pusty** projekt.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Zmień nazwę projektu, jeśli chcesz, a następnie wybierz **przycisk** Utwórz.

::: moniker-end
4. Na stronie **Określanie** lokacji i poziomu zabezpieczeń na potrzeby debugowania określ adres URL  witryny programu SharePoint na komputerze lokalnym, wybierz przycisk Wdeń jako rozwiązanie farmy, a następnie wybierz przycisk **Zakończ.**

     Model zostanie przetestowany w określonej witrynie programu SharePoint.

    > [!IMPORTANT]
    > Projekt należy wdrożyć jako rozwiązanie farmy, ponieważ modele BDC obsługują tylko rozwiązania farmy.

     Zostanie utworzony pusty projekt programu SharePoint.

5. Na pasku menu wybierz pozycję **Projekt**  >  **Dodaj nowy element.**

6. W **oknie dialogowym** Dodawanie nowego elementu wybierz węzeł **Office/SharePoint.**

7. Na liście szablonów programu SharePoint wybierz pozycję Model łączności danych biznesowych **(tylko rozwiązanie farmy).**

8. W polu **Nazwa** określ nazwę modelu BDC, a następnie wybierz **przycisk** Dodaj.

     Do projektu zostanie dodany **element Model** łączności danych biznesowych. Domyślnie model jest wyświetlany w projektancie BDC. Aby uzyskać więcej informacji, zobacz [Create a business data connectivity model (Tworzenie modelu łączności danych biznesowych).](../sharepoint/creating-a-business-data-connectivity-model.md)

## <a name="see-also"></a>Zobacz też

- [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Jak dodać istniejący plik modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Jak użyć pliku zasobu do określenia zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [How to: Include a custom assembly in a BDC feature (Jak uwzględnić zestaw niestandardowy w funkcji BDC)](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrowanie danych biznesowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
