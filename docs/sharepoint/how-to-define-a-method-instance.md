---
title: 'Instrukcje: Definiowanie wystąpienia metody | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 2f879f8367ad1b992300c9e5b1c8a2887e89205b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608015"
---
# <a name="how-to-define-a-method-instance"></a>Instrukcje: Definiowanie wystąpienia metody
  Należy zdefiniować co najmniej jedno wystąpienie metody dla każdej metody w modelu.

 Dodaj wystąpienie metody przy użyciu **szczegóły metody BDC** okna. Po dodaniu wystąpienie metody, program Visual Studio dodaje `<MethodInstance>` — element XML w pliku modelu w twoim projekcie. Aby uzyskać więcej informacji na temat atrybutów `<MethodInstance>` elementu, zobacz [elementu MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).

### <a name="to-define-a-method-instance"></a>Aby zdefiniować wystąpienie metody

1.  W **szczegóły metody BDC** okna, rozwiń węzeł metody, a następnie rozwiń **wystąpień** węzła.

2.  W **Dodaj wystąpienie metody** wybierz **Utwórz wystąpienie metody wyszukującej**.

     Nowe wystąpienie metody zostanie wyświetlone poniżej **wystąpień** węzła.

3.  Na pasku menu wybierz **widoku** > **okno właściwości**.

4.  W **właściwości** okna, ustaw właściwości wystąpienia metody. Aby uzyskać więcej informacji na temat każdej właściwości, zobacz [elementu MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).

## <a name="see-also"></a>Zobacz także
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Instrukcje: Dodaj parametr do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)
