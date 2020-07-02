---
title: Programowe buforowanie źródła danych w dokumencie pakietu Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ec3a38d109de561e3cba77951764dd8dd9479df
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544771"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Instrukcje: programowane buforowanie źródła danych w dokumencie pakietu Office
  Można programowo dodać obiekt danych do pamięci podręcznej danych w dokumencie, wywołując `StartCaching` metodę elementu hosta, taką jak <xref:Microsoft.Office.Tools.Word.Document> , <xref:Microsoft.Office.Tools.Excel.Workbook> , lub <xref:Microsoft.Office.Tools.Excel.Worksheet> . Usuń obiekt danych z pamięci podręcznej danych, wywołując `StopCaching` metodę elementu hosta.

 `StartCaching`Metoda i `StopCaching` Metoda są jednocześnie prywatne, ale są wyświetlane w technologii IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Gdy używasz `StartCaching` metody do dodawania obiektu danych do pamięci podręcznej danych, obiekt danych nie musi być zadeklarowany z <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutem. Jednak obiekt danych musi spełniać pewne wymagania, aby można je było dodać do pamięci podręcznej danych. Aby uzyskać więcej informacji, zobacz [cache Data](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Aby programowo przetworzyć obiekt danych w pamięci podręcznej

1. Zadeklaruj obiekt danych na poziomie klasy, a nie wewnątrz metody. W tym przykładzie założono, że deklarujesz <xref:System.Data.DataSet> nazwę `dataSet1` , która ma być programowo buforowana.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Utwórz wystąpienie obiektu danych, a następnie Wywołaj `StartCaching` metodę wystąpienia dokumentu lub arkusza i przekaż nazwę obiektu danych.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Aby zatrzymać buforowanie obiektu danych

1. Wywołaj `StopCaching` metodę w wystąpieniu dokumentu lub arkusza i przekaż nazwę obiektu danych. W tym przykładzie przyjęto założenie, że istnieje <xref:System.Data.DataSet> nazwa `dataSet1` , która ma zostać zatrzymana.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > Nie wywołuj `StopCaching` z programu obsługi zdarzeń dla `Shutdown` zdarzenia dokumentu lub arkusza. Przez czas, gdy `Shutdown` zdarzenie jest zgłaszane, zbyt późno na modyfikację pamięci podręcznej danych. Aby uzyskać więcej informacji o `Shutdown` zdarzeniu, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Zobacz także

- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Instrukcje: dane z pamięci podręcznej do użycia w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Instrukcje: buforowanie danych w dokumencie chronionym hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)
- [Zapisywanie danych](../data-tools/save-data-back-to-the-database.md)
