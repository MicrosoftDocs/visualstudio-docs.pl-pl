---
title: Zapisywanie zestawu danych jako XML | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 49fb600b2c27725eb6fe888aa2a41a6b19c123b0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785144"
---
# <a name="save-a-dataset-as-xml"></a>Zapisywanie zestawu danych jako kodu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Przez wywołanie metody dostępne metody XML zestawu danych można uzyskać dostępu do danych XML w zestawie danych. Aby zapisać dane w formacie XML, należy wywołać albo <xref:System.Data.DataSet.GetXml%2A> metody lub <xref:System.Data.DataSet.WriteXml%2A> metody <xref:System.Data.DataSet>.  
  
 Wywoływanie <xref:System.Data.DataSet.GetXml%2A> metoda zwraca ciąg, który zawiera dane ze wszystkich tabel danych w zestawie danych, który jest w formacie XML.  
  
 Wywoływanie <xref:System.Data.DataSet.WriteXml%2A> metoda wysyła dane w formacie XML do pliku, który określisz.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Aby zapisać dane w zestawie danych jako XML do zmiennej  
  
-   <xref:System.Data.DataSet.GetXml%2A> Metoda zwraca <xref:System.String>. Oznacza to, że Deklarujesz zmienną typu <xref:System.String> i przypisać jej wyniki <xref:System.Data.DataSet.GetXml%2A> metody.  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Aby zapisać dane w zestawie danych jako XML do pliku  
  
-   <xref:System.Data.DataSet.WriteXml%2A> Metoda ma kilka przeciążeń. Poniższy kod przedstawia sposób zapisywania danych do pliku. Zadeklaruj zmienną i przypisać ją prawidłową ścieżkę, aby zapisać plik.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
