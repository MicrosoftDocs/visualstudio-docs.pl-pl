---
title: Zapisywanie zestawu danych jako kodu XML
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5b3aa23cb0fde98b4da4225b8e255b7cd6e7aef5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641352"
---
# <a name="save-a-dataset-as-xml"></a>Zapisywanie zestawu danych jako kodu XML

Dostęp do danych XML w zestawie danych przez wywołanie dostępnych metod XML w zestawie danych. Aby zapisać dane w formacie XML, można wywołać metodę <xref:System.Data.DataSet.GetXml%2A> lub <xref:System.Data.DataSet.WriteXml%2A> metodę <xref:System.Data.DataSet>.

Wywołanie metody <xref:System.Data.DataSet.GetXml%2A> zwraca ciąg, który zawiera dane ze wszystkich tabel danych w zestawie danych, który jest sformatowany jako XML.

Wywołanie metody <xref:System.Data.DataSet.WriteXml%2A> wysyła dane sformatowane w formacie XML do określonego pliku.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Aby zapisać dane w zestawie danych jako XML do zmiennej

- Metoda <xref:System.Data.DataSet.GetXml%2A> zwraca <xref:System.String>. Zadeklaruj zmienną typu <xref:System.String> i przypisz jej wyniki metody <xref:System.Data.DataSet.GetXml%2A>.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Aby zapisać dane w zestawie danych jako XML do pliku

- Metoda <xref:System.Data.DataSet.WriteXml%2A> ma kilka przeciążeń. Zadeklaruj zmienną i przypisz ją do prawidłowej ścieżki, aby zapisać plik w. Poniższy kod przedstawia sposób zapisywania danych do pliku:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)