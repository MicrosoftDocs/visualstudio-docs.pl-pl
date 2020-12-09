---
title: 'Instrukcje: Dodawanie parametru do metody | Microsoft Docs'
description: Dowiedz się, jak dodać parametr do metody łączności danych biznesowych (BDC), która umożliwia przekazywanie informacji do metody lub zwracanie informacji z metody.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 179109ff4c0def002dac45887fe9491196a70d3e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915404"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Instrukcje: Dodawanie parametru do metody
  Użyj parametru, aby przekazać informacje do metody lub zwrócić informacje z metody. Wszystkie metody muszą mieć co najmniej jeden parametr. Aby uzyskać więcej informacji na temat projektowania parametru do obsługi typu metody, którą chcesz utworzyć, zobacz [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md).

 Po dodaniu parametru do metody program Visual Studio dodaje element Parameter do pliku XML w projekcie. Aby uzyskać więcej informacji na temat atrybutów elementu parametru, zobacz [parametr](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14)).

### <a name="to-add-a-parameter-to-a-method"></a>Aby dodać parametr do metody

1. Dodaj metodę do jednostki.

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  >  **Szczegóły metody BDC** systemu Windows.

     Zostanie otwarte okno **Szczegóły metody BDC** . Aby uzyskać więcej informacji, zobacz [Omówienie narzędzi projektowania modelu usługi BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. W oknie **Szczegóły metody BDC** rozwiń węzeł metody, a następnie rozwiń węzeł **Parametry** .

4. Na liście **Dodaj parametr** wybierz pozycję **Utwórz parametr**.

     Nowy parametr zostanie wyświetlony poniżej węzła **Parameters** .

5. Na pasku menu wybierz **View**  >  **okno właściwości** widoku.

6. W oknie **Właściwości** ustaw właściwość **Nazwa** na dowolną nazwę, która ma sens. Na przykład jeśli metoda zwróci klientów, można nazwać metodę **Getcustomerss**.

7. W oknie **Szczegóły metody BDC** Otwórz listę, która jest wyświetlana dla kierunku parametru, a następnie wybierz **w**, **Inout**, **out** lub **Return**.

     Aby uzyskać więcej informacji na temat tego, który kierunek jest wybierany dla tworzonej metody typu, zobacz [Projektowanie modelu łączności danych firmowych](../sharepoint/designing-a-business-data-connectivity-model.md).

8. Modyfikuj deskryptor typu parametru. Aby uzyskać więcej informacji, zobacz [How to: define The Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Instrukcje: Definiowanie deskryptora typu dla parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
