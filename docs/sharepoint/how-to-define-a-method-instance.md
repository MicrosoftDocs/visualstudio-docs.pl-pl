---
title: 'Instrukcje: Definiowanie wystąpienia metody | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 170982a5d4abe33ca8cd705a979acc0737185a9c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016828"
---
# <a name="how-to-define-a-method-instance"></a>Instrukcje: Definiowanie wystąpienia metody
  Należy zdefiniować co najmniej jedno wystąpienie metody dla każdej metody w modelu.

 Dodaj wystąpienie metody przy użyciu okna **Szczegóły metody BDC** . Po dodaniu wystąpienia metody program Visual Studio dodaje `<MethodInstance>` element do pliku XML w projekcie. Aby uzyskać więcej informacji na temat atrybutów `<MethodInstance>` elementu, zobacz [Klasa MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>Aby zdefiniować wystąpienie metody

1. W oknie **Szczegóły metody BDC** rozwiń węzeł metody, a następnie rozwiń węzeł **Instances (wystąpienia** ).

2. Na liście **Dodaj wystąpienie metody** wybierz pozycję **Utwórz wystąpienie wyszukiwania**.

     Nowe wystąpienie metody pojawi się poniżej węzła **Instances** .

3. Na pasku menu wybierz **View**  >  **okno właściwości**widoku.

4. W oknie **Właściwości** ustaw właściwości wystąpienia metody. Aby uzyskać więcej informacji na temat każdej właściwości, zobacz element [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>Zobacz także
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie deskryptora typu dla parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
