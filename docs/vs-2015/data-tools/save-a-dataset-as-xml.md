---
title: Zapisywanie zestawu danych jako XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e64c3c17934e5cdc5d6ca1f510c7164b86a77c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652863"
---
# <a name="save-a-dataset-as-xml"></a>Zapisywanie zestawu danych jako kodu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dostęp do danych XML w zestawie danych można uzyskać, wywołując dostępne metody XML dla zestawu danych. Aby zapisać dane w formacie XML, można wywołać <xref:System.Data.DataSet.GetXml%2A> metodę lub <xref:System.Data.DataSet.WriteXml%2A> metodę <xref:System.Data.DataSet> .

 Wywołanie <xref:System.Data.DataSet.GetXml%2A> metody zwraca ciąg, który zawiera dane ze wszystkich tabel danych w zestawie danych, który jest sformatowany jako XML.

 Wywołanie <xref:System.Data.DataSet.WriteXml%2A> metody wysyła dane sformatowane w formacie XML do określonego pliku.

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Aby zapisać dane w zestawie danych jako XML do zmiennej

- <xref:System.Data.DataSet.GetXml%2A>Metoda zwraca <xref:System.String> . Oznacza to, że deklarujesz zmienną typu <xref:System.String> i przypiszesz jej wyniki <xref:System.Data.DataSet.GetXml%2A> metody.

     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Aby zapisać dane w zestawie danych jako XML do pliku

- <xref:System.Data.DataSet.WriteXml%2A>Metoda ma kilka przeciążeń. Poniższy kod przedstawia sposób zapisywania danych do pliku. Zadeklaruj zmienną i przypisz ją do prawidłowej ścieżki, aby zapisać plik w.

     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]

## <a name="see-also"></a>Zobacz też
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
