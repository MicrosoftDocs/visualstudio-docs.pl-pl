---
title: 'Instrukcje: Dodaj parametr do metody | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f7d0e0ab164bf30c341ca093908be3661452d19
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866260"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Instrukcje: Dodaj parametr do metody
  Parametru można użyć do przekazywania informacji do metody, lub aby zostały zwrócone informacje z metody. Wszystkie metody musi mieć co najmniej jeden parametr. Aby uzyskać więcej informacji na temat projektowania parametr obsługuje typu metody, która ma zostać utworzona, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Po dodaniu parametru do metody programu Visual Studio dodaje element parametru do XML w pliku modelu w twoim projekcie. Aby uzyskać więcej informacji na temat atrybutów elementu parametru zobacz [parametru](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Aby dodać parametr do metody  
  
1.  Dodaj metodę do jednostki.  
  
2.  Na pasku menu wybierz **widoku** > **Windows inne** > **szczegóły metody BDC**.  
  
     **Szczegóły metody BDC** zostanie otwarte okno. Aby uzyskać więcej informacji, zobacz [omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  W **szczegóły metody BDC** okna, rozwiń węzeł metody, a następnie rozwiń **parametry** węzła.  
  
4.  W **dodać parametr** wybierz **tworzenie parametru**.  
  
     Nowy parametr wyświetlany pod **parametry** węzła.  
  
5.  Na pasku menu wybierz **widoku** > **okno właściwości**.  
  
6.  W **właściwości** oknie **nazwa** właściwości z nazwą pasującą. Na przykład, jeśli metoda zwróci dane klientów, można nazwać metody **GetCustomers**.  
  
7.  W **szczegóły metody BDC** okna, Otwórz listę, która pojawia się dla Kierunek parametru, a następnie wybierz **w**, **InOut**, **się**, lub **zwracają**.  
  
     Aby uzyskać więcej informacji na temat kierunek, w którym należy wybrać dla metody typu, który tworzysz, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Zmodyfikuj deskryptor typu parametru. Aby uzyskać więcej informacji, zobacz [jak: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Zobacz także
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Instrukcje: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)  
