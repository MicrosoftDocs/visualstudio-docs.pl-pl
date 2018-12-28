---
title: 'Instrukcje: Programowe buforowanie źródła danych w dokumencie programu Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3db60729facffdfd42553f95215e154de528436f
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804448"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Instrukcje: Programowe buforowanie źródła danych w dokumencie programu Word
  Obiekt danych można programowo dodać do pamięci podręcznej danych w dokumencie, przez wywołanie metody `StartCaching` metoda hosta elementów, takich jak <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, lub <xref:Microsoft.Office.Tools.Excel.Worksheet>. Usuń obiekt danych z pamięci podręcznej danych przez wywołanie metody `StopCaching` metoda element hosta.

 `StartCaching` Metody i `StopCaching` metody są prywatne, ale są one wyświetlane w IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Kiedy używasz `StartCaching` metodę, aby dodać obiekt danych do pamięci podręcznej danych obiektu danych nie musi być zadeklarowana z <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu. Jednak obiekt danych musi spełniać określone wymagania, które mają zostać dodane do pamięci podręcznej danych. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Programowe buforowanie obiektu danych

1.  Należy zadeklarować obiekt danych na poziomie klasy, nie wewnątrz metody. W tym przykładzie przyjęto założenie, użytkownik deklaruje <xref:System.Data.DataSet> o nazwie `dataSet1` , którą chcesz buforować programowo.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2.  Utwórz wystąpienie obiektu danych, a następnie wywołaj `StartCaching` metoda dokumencie lub arkuszu wystąpienia i nazwę obiektu danych.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Aby zatrzymać buforowanie obiektu danych

1.  Wywołaj `StopCaching` metoda dokumencie lub arkuszu wystąpienia i nazwę obiektu danych. W tym przykładzie przyjęto założenie, iż <xref:System.Data.DataSet> o nazwie `dataSet1` , którą chcesz zatrzymać buforowania.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    >  Nie wywołuj `StopCaching` z programu obsługi zdarzeń `Shutdown` zdarzenia dokument lub skoroszyt. Do czasu `Shutdown` zdarzenie jest zgłaszane, jest za późno, aby zmodyfikować pamięci podręcznej danych. Aby uzyskać więcej informacji na temat `Shutdown` zdarzeń, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Zobacz także

- [Dane w pamięci podręcznej](../vsto/caching-data.md)
- [Instrukcje: Dane z pamięci podręcznej do użytku w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Instrukcje: Dane w pamięci podręcznej w dokumentach zabezpieczonych hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)
- [Zapisywanie danych](../data-tools/saving-data.md)
