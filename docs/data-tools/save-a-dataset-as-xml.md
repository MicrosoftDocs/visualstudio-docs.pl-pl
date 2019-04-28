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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c993ac8703468a24a99e114563fec1bdc817581
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566231"
---
# <a name="save-a-dataset-as-xml"></a>Zapisywanie zestawu danych jako kodu XML

Dostęp do danych XML w zestawie danych, wywołując dostępnych metod XML zestawu danych. Aby zapisać dane w formacie XML, należy wywołać albo <xref:System.Data.DataSet.GetXml%2A> metody lub <xref:System.Data.DataSet.WriteXml%2A> metody <xref:System.Data.DataSet>.

Wywoływanie <xref:System.Data.DataSet.GetXml%2A> metoda zwraca ciąg, który zawiera dane ze wszystkich tabel danych w zestawie danych, który jest w formacie XML.

Wywoływanie <xref:System.Data.DataSet.WriteXml%2A> metoda wysyła dane w formacie XML do pliku, który określisz.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Aby zapisać dane w zestawie danych jako XML do zmiennej

- <xref:System.Data.DataSet.GetXml%2A> Metoda zwraca <xref:System.String>. Zadeklaruj zmienną typu <xref:System.String> i przypisać jej wyniki <xref:System.Data.DataSet.GetXml%2A> metody.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Aby zapisać dane w zestawie danych jako XML do pliku

- <xref:System.Data.DataSet.WriteXml%2A> Metoda ma kilka przeciążeń. Zadeklaruj zmienną i przypisać ją prawidłową ścieżkę, aby zapisać plik. Poniższy kod pokazuje sposób zapisywania danych do pliku:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)