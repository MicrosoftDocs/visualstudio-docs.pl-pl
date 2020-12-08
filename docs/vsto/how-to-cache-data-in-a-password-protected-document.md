---
title: 'Instrukcje: buforowanie danych w dokumencie chronionym hasłem'
description: Dowiedz się, że jeśli dodasz dane do pamięci podręcznej danych w dokumencie lub skoroszycie chronionym hasłem, możesz zapisać zmiany w pamięci podręcznej, zastępując dwie metody w projekcie.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 2a11b70da4bdd2500f70d2b45f025340af21ea94
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846002"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Instrukcje: buforowanie danych w dokumencie chronionym hasłem
  W przypadku dodania danych do pamięci podręcznej danych w dokumencie lub skoroszycie chronionym hasłem zmiany w buforowanych danych nie są zapisywane automatycznie. Zmiany w buforowanych danych można zapisać przez zastępowanie dwóch metod w projekcie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Buforowanie w dokumentach programu Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Aby buforować dane w dokumencie programu Word chronionym hasłem

1. W `ThisDocument` klasie Oznacz pole publiczne lub właściwość, które mają być buforowane. Aby uzyskać więcej informacji, zobacz [cache Data](../vsto/caching-data.md).

2. Zastąp <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodę w `ThisDocument` klasie i Usuń ochronę z dokumentu.

     Gdy dokument zostanie zapisany, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę, aby dać Ci możliwość usunięcia ochrony dokumentu. Dzięki temu zmiany mają być zapisywane dane buforowane.

3. Zastąp <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodę w `ThisDocument` klasie i ponownie Zastosuj ochronę do dokumentu.

     Po zapisaniu dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołanie tej metody daje możliwość ponownego zastosowania ochrony do dokumentu.

### <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje sposób buforowania danych w dokumencie programu Word, który jest chroniony hasłem. Przed usunięciem ochrony w <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodzie zapisuje bieżącą <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> wartość, dzięki czemu można ponownie zastosować ten sam typ ochrony w <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodzie.

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Kompiluj kod
 Dodaj ten kod do `ThisDocument` klasy w projekcie. W tym kodzie założono, że hasło jest przechowywane w polu o nazwie `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Buforowanie w skoroszytach programu Excel
 W projektach programu Excel ta procedura jest niezbędna tylko w przypadku ochrony całego skoroszytu hasłem przy użyciu <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metody. Ta procedura nie jest konieczna w przypadku ochrony tylko określonego arkusza z hasłem przy użyciu <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metody.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Aby buforować dane w skoroszycie programu Excel chronionym hasłem

1. W `ThisWorkbook` klasie lub jednej z `Sheet` *n* klas zaznacz pole publiczne lub właściwość, które mają być buforowane. Aby uzyskać więcej informacji, zobacz [cache Data](../vsto/caching-data.md).

2. Zastąp <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodę w `ThisWorkbook` klasie i Usuń ochronę ze skoroszytu.

     Gdy skoroszyt zostanie zapisany, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę, aby dać Ci możliwość usunięcia ochrony skoroszytu. Dzięki temu zmiany mają być zapisywane dane buforowane.

3. Zastąp <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodę w `ThisWorkbook` klasie i ponownie Zastosuj ochronę do dokumentu.

     Po zapisaniu skoroszytu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wywołuje tę metodę, aby dać Ci możliwość ponownego zastosowania ochrony skoroszytu.

### <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje sposób buforowania danych w skoroszycie programu Excel, który jest chroniony hasłem. Przed usunięciem ochrony w <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodzie zapisuje ona bieżące <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> i <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> wartości, dzięki czemu można ponownie zastosować ten sam typ ochrony w <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodzie.

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Kompiluj kod
 Dodaj ten kod do `ThisWorkbook` klasy w projekcie. W tym kodzie założono, że hasło jest przechowywane w polu o nazwie `securelyStoredPassword` .

## <a name="see-also"></a>Zobacz także
- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Instrukcje: dane z pamięci podręcznej do użycia w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Instrukcje: programowane buforowanie źródła danych w dokumencie pakietu Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
