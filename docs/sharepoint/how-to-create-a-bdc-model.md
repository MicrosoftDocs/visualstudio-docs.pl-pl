---
title: 'Instrukcje: Tworzenie modelu BDC | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: d82678df0da5932dd33c08a6e3066462df204f6e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596506"
---
# <a name="how-to-create-a-bdc-model"></a>Instrukcje: Tworzenie modelu BDC
  Model łączności danych biznesowych (BDC) można utworzyć za pomocą szablonu dla tego rodzaju elementu, a następnie dodania modelu do każdego projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md). Aby uzyskać więcej informacji na temat projektowania modelu, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-bdc-project"></a>Aby utworzyć projekt BDC

1.  Na pasku menu wybierz **pliku** > **New** > **projektu**.

    > [!NOTE]
    >  Jeśli środowisko IDE jest ustawione do użycia z ustawieniami środowiska deweloperskiego Visual Basic, wybierz opcję **pliku** > **nowy projekt**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

2.  W obszarze **języka Visual Basic** lub **Visual C#** , wybierz **Office/SharePoint**, **rozwiązań programu SharePoint**.

3.  W **szablony** okienku wybierz **SharePoint 2013 — pusty projekt** elementu, a następnie wybierz **OK** przycisku.

     **Kreator ustawień niestandardowych SharePoint** zostanie otwarty.

4.  Na **Określanie witryny i poziomu zabezpieczeń dla debugowania** strony, podaj adres URL witryny programu SharePoint na komputerze lokalnym, wybierz **Wdróż rozwiązanie farmy** przycisk opcji, a następnie wybierz **Zakończ** przycisku.

     Możesz testować model w witrynie programu SharePoint, który określiłeś.

    > [!IMPORTANT]
    >  Ponieważ modele usługi BDC obsługują tylko rozwiązaniami farmy, należy wdrożyć projekt jako rozwiązanie farmy.

     Pusty projekt programu SharePoint jest tworzony.

5.  Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

6.  W **Dodaj nowy element** okna dialogowego wybierz **Office/SharePoint** węzła.

7.  Na liście szablonów programu SharePoint, wybierz opcję **modelu łączności danych biznesowych (tylko rozwiązanie farmy)**.

8.  W **nazwa** pola, określ nazwę dla modelu usługi łączności danych biznesowych, a następnie wybierz **Dodaj** przycisku.

     A **Model usługi łączności danych biznesowych** element zostanie dodany do projektu. Domyślnie model pojawia się w Projektancie usługi łączności danych biznesowych. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Zobacz także
- [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Instrukcje: Dodawanie istniejącego modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Instrukcje: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Instrukcje: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
