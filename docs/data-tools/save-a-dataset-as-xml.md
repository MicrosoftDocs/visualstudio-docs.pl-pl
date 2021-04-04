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
ms.openlocfilehash: 42974852a3051fd3473b6b23d880eeb38b966b95
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216205"
---
# <a name="save-a-dataset-as-xml"></a>Zapisywanie zestawu danych jako kodu XML

Dostęp do danych XML w zestawie danych przez wywołanie dostępnych metod XML w zestawie danych. Aby zapisać dane w formacie XML, można wywołać <xref:System.Data.DataSet.GetXml%2A> metodę lub <xref:System.Data.DataSet.WriteXml%2A> metodę <xref:System.Data.DataSet> .

Wywołanie <xref:System.Data.DataSet.GetXml%2A> metody zwraca ciąg, który zawiera dane ze wszystkich tabel danych w zestawie danych, który jest sformatowany jako XML.

Wywołanie <xref:System.Data.DataSet.WriteXml%2A> metody wysyła dane sformatowane w formacie XML do określonego pliku.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Aby zapisać dane w zestawie danych jako XML do zmiennej

- <xref:System.Data.DataSet.GetXml%2A>Metoda zwraca <xref:System.String> . Zadeklaruj zmienną typu <xref:System.String> i przypisz ją do wyników <xref:System.Data.DataSet.GetXml%2A> metody.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet12":::

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Aby zapisać dane w zestawie danych jako XML do pliku

- <xref:System.Data.DataSet.WriteXml%2A>Metoda ma kilka przeciążeń. Zadeklaruj zmienną i przypisz ją do prawidłowej ścieżki, aby zapisać plik w. Poniższy kod przedstawia sposób zapisywania danych do pliku:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet13":::

## <a name="see-also"></a>Zobacz też

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
