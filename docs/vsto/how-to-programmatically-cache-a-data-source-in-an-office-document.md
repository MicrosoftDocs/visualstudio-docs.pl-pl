---
title: Programowe buforowanie źródła danych w dokumencie pakietu Office
description: Dowiedz się, jak programowo dodać obiekt danych do pamięci podręcznej danych w dokumencie, wywołując metodę StartCaching elementu hosta.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 070253fb7ec57bedad628e116ce193fa2d9cf50b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827594"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Jak programowo buforować źródło danych w dokumencie pakietu Office
  Obiekt danych można programowo dodać do pamięci podręcznej danych w dokumencie, wywołując metodę elementu hosta, taką jak `StartCaching` <xref:Microsoft.Office.Tools.Word.Document> , lub <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> . Usuń obiekt danych z pamięci podręcznej danych, `StopCaching` wywołując metodę elementu hosta.

 Zarówno `StartCaching` metoda, jak `StopCaching` i metoda są prywatne, ale pojawiają się w funkcji IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Gdy używasz metody do dodawania obiektu danych do pamięci podręcznej danych, obiekt danych nie musi być zadeklarowany `StartCaching` za pomocą <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu . Jednak obiekt danych musi spełniać pewne wymagania, które należy dodać do pamięci podręcznej danych. Aby uzyskać więcej informacji, zobacz [Dane pamięci podręcznej](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Aby programowo buforować obiekt danych

1. Zadeklaruj obiekt danych na poziomie klasy, a nie wewnątrz metody. W tym przykładzie przyjęto założenie, że deklarowany jest <xref:System.Data.DataSet> `dataSet1` nazwany, który ma być buforowany programowo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet12":::

2. Wystąpienie obiektu danych, a następnie wywołanie metody wystąpienia dokumentu lub arkusza i podanie `StartCaching` nazwy obiektu danych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet13":::

## <a name="to-stop-caching-a-data-object"></a>Aby zatrzymać buforowanie obiektu danych

1. Wywołaj metodę wystąpienia dokumentu lub arkusza i przekaż `StopCaching` nazwę obiektu danych. W tym przykładzie przyjęto założenie, że masz <xref:System.Data.DataSet> `dataSet1` nazwę, której chcesz zatrzymać buforowanie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet14":::

    > [!NOTE]
    > Nie `StopCaching` wywołuj z procedury obsługi zdarzeń zdarzenia dokumentu lub `Shutdown` arkusza. Do czasu, `Shutdown` gdy zdarzenie jest wywoływane, jest za opóźniona, aby zmodyfikować pamięć podręczną danych. Aby uzyskać więcej informacji o `Shutdown` zdarzeniu, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)

## <a name="see-also"></a>Zobacz też

- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Jak buforować dane do użytku w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [How to: Cache data in a password-protected document (Jak buforować dane w dokumencie chronionym hasłem)](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)
- [Zapisywanie danych](../data-tools/save-data-back-to-the-database.md)
