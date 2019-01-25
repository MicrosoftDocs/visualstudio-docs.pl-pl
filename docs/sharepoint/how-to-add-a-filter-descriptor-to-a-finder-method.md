---
title: 'Instrukcje: Dodawanie opisu filtru do metody wyszukiwania | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f21cecee163b6d79d22d008314c0dcf54a313032
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866142"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Instrukcje: Dodawanie opisu filtru do metody wyszukiwania
  Deskryptory filtrów umożliwiają użytkownikom modelu do przekazania wartości do metod, przed ich wykonania. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Jeden typowy scenariusz polega na tym, że użytkownicy w programie SharePoint ma zostać pobrane wystąpienia typu zawartości zewnętrznej, które spełniają pewne kryteria. Aby obsługiwać ten scenariusz, dodawanie deskryptora filtru do metody wyszukiwania.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Aby dodać Deskryptor filtru do metody wyszukiwania  
  
1.  W **szczegóły metody BDC** okna, rozwiń węzeł metody wyszukiwania, rozwiń **parametry** węzła, a następnie dodaj parametr wejściowy. Aby uzyskać więcej informacji, zobacz [jak: Dodaj parametr do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  W **szczegóły metody** oknie Wybierz deskryptor typu parametru.  
  
3.  Na pasku menu wybierz **widoku** > **okno właściwości**.  
  
4.  W **właściwości** oknie **nazwy typu** właściwość do typu danych, która jest odpowiednia dla filtru.  
  
     Filtr może na przykład użyć datę zamówienia, aby ograniczyć liczbę zamówień sprzedaży, zwracany przez metodę. Do obsługi z filtrem **nazwy typu** właściwości deskryptora typu musi być równa **System.DateTime**.  
  
5.  W **szczegóły metody** okna, rozwiń węzeł **deskryptory filtrów** węzła.  
  
6.  W **Dodaj Deskryptor filtru** wybierz **Utwórz Deskryptor filtru**.  
  
     Nowy Deskryptor filtru, który pojawia się poniżej **deskryptory filtrów** węzła.  
  
7.  Na pasku menu wybierz **widoku** > **okno właściwości**.  
  
8.  W **właściwości** oknie Wybierz **typu** właściwości.  
  
9. Na liście, który pojawia się dla **typu** właściwości filtrowania wzorzec, który chcesz wybrać.  
  
     Na przykład, aby utworzyć filtr, który używa datę zamówienia, aby ograniczyć liczbę zamówień sprzedaży zwrócony w metodę wyszukiwania, wybierz **porównania**. Filtr porównywania gwarantuje, że metody wyszukiwania zwraca tylko te wystąpienia, które spełniają określony warunek. Aby uzyskać więcej informacji na temat każdego wzorca filtrowania zobacz [typy z filtrów obsługiwane przez usługi łączności danych biznesowych](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. W **właściwości** oknie Wybierz **skojarzone deskryptory typu** właściwości.  
  
11. Na liście, który pojawia się dla **skojarzone deskryptory typu** właściwości, wybierz deskryptor typu, który został utworzony we wcześniejszej części tej procedury. Filtr odnosi się do parametru wejściowego metody wyszukiwania.  
  
12. Dodaj kod do metody wyszukiwania, która zwraca dane. Parametr wejściowy służy jako warunku w zapytaniu select.  
  
     Poniższy przykład zwraca zamówień sprzedaży, datą w określonej kolejności.  
  
    > [!NOTE]  
    >  Zastąp wartość `ServerName` pole z nazwą serwera.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Instrukcje: Dodaj parametr do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Instrukcje: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
