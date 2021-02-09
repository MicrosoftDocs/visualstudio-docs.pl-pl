---
title: Zapisywanie zestawu danych jako kodu XML
description: Zapisz zestaw danych jako XML. Dostęp do danych XML w zestawie danych przez wywołanie dostępnych metod XML na zestawie danych, takich jak GetXml — lub WriteXml.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9030740a25312ea1463b950e34061884e9487ba4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858530"
---
# <a name="save-a-dataset-as-xml"></a>Zapisywanie zestawu danych jako kodu XML

Dostęp do danych XML w zestawie danych przez wywołanie dostępnych metod XML w zestawie danych. Aby zapisać dane w formacie XML, można wywołać <xref:System.Data.DataSet.GetXml%2A> metodę lub <xref:System.Data.DataSet.WriteXml%2A> metodę <xref:System.Data.DataSet> .

Wywołanie <xref:System.Data.DataSet.GetXml%2A> metody zwraca ciąg, który zawiera dane ze wszystkich tabel danych w zestawie danych, który jest sformatowany jako XML.

Wywołanie <xref:System.Data.DataSet.WriteXml%2A> metody wysyła dane sformatowane w formacie XML do określonego pliku.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Aby zapisać dane w zestawie danych jako XML do zmiennej

- <xref:System.Data.DataSet.GetXml%2A>Metoda zwraca <xref:System.String> . Zadeklaruj zmienną typu <xref:System.String> i przypisz ją do wyników <xref:System.Data.DataSet.GetXml%2A> metody.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Aby zapisać dane w zestawie danych jako XML do pliku

- <xref:System.Data.DataSet.WriteXml%2A>Metoda ma kilka przeciążeń. Zadeklaruj zmienną i przypisz ją do prawidłowej ścieżki, aby zapisać plik w. Poniższy kod przedstawia sposób zapisywania danych do pliku:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
