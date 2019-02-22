---
title: 'Instrukcje: Dane w pamięci podręcznej w dokumentach zabezpieczonych hasłem'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f6e9bea3d45249d847f2dccfe522f832d6a07b5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644526"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Instrukcje: Dane w pamięci podręcznej w dokumentach zabezpieczonych hasłem
  Możesz dodać dane do pamięci podręcznej danych na dokument lub skoroszyt, który jest chroniony hasłem, zmiany w buforowanych danych nie są zapisywane automatycznie. Aby zapisać zmiany na dane w pamięci podręcznej, zastępowanie dwie metody w projekcie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Buforowanie w dokumentach programu Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Do buforowania danych w dokumencie programu Word, który jest chroniony hasłem

1.  W `ThisDocument` klasy, oznacz publiczne pole lub właściwość przechowywanie w pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).

2.  Zastąp <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> method in Class metoda `ThisDocument` klasy i usuwanie ochrony z dokumentu.

     Po zapisaniu dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę w celu zapewniają możliwość wyłączania ochrony dokumentu. Dzięki temu zmiany mają być zapisywane dane buforowane.

3.  Zastąp <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> method in Class metoda `ThisDocument` klasy i ponownie zastosować ochronę dokumentu.

     Po zapisaniu dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę, aby zapewnić możliwość ponownego zastosowania ochrony do dokumentu.

### <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak buforowanie danych w dokumencie programu Word, który jest chroniony hasłem. Zanim kod usuwa ochrony w <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metody zapisuje bieżący <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> wartość tak, aby móc ponownie zastosować ten sam typ ochrony w <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metody.

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Skompilować kod
 Dodaj następujący kod do `ThisDocument` klasy w projekcie. Ten kod zakłada, że hasło jest przechowywane w polu o nazwie `securelyStoredPassword`.

## <a name="cache-in-excel-workbooks"></a>Pamięć podręczna w skoroszytach programu Excel
 W projektach programu Excel, ta procedura jest niezbędna tylko wtedy, gdy cały skoroszyt za pomocą hasła jest chroniony przy użyciu <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metody. Ta procedura nie jest konieczne, jeśli chroniony określonego arkusza za pomocą hasła przy użyciu <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metody.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Do buforowania danych w skoroszycie programu Excel, który jest chroniony hasłem

1.  W `ThisWorkbook` klasy lub jednej z `Sheet` *n* klas, oznacz publiczne pole lub właściwość przechowywanie w pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).

2.  Zastąp <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> method in Class metoda `ThisWorkbook` klasy, a następnie usuń ochronę skoroszytu.

     Po zapisaniu skoroszytu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę, aby zapewnić możliwość usuwające ochronę skoroszytu. Dzięki temu zmiany mają być zapisywane dane buforowane.

3.  Zastąp <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> method in Class metoda `ThisWorkbook` klasy i ponownie zastosować ochronę dokumentu.

     Po zapisaniu skoroszytu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę daje możliwość ponownego zastosowania ochrony do skoroszytu.

### <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak buforowanie danych w skoroszycie programu Excel, który jest chroniony hasłem. Zanim kod usuwa ochrony w <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metody zapisuje bieżący <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> i <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> wartości, tak aby móc ponownie zastosować ten sam typ ochrony w <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metody.

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Skompilować kod
 Dodaj następujący kod do `ThisWorkbook` klasy w projekcie. Ten kod zakłada, że hasło jest przechowywane w polu o nazwie `securelyStoredPassword`.

## <a name="see-also"></a>Zobacz także
- [Dane w pamięci podręcznej](../vsto/caching-data.md)
- [Instrukcje: Dane z pamięci podręcznej do użytku w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Instrukcje: Programowe buforowanie źródła danych w dokumencie programu Word](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
