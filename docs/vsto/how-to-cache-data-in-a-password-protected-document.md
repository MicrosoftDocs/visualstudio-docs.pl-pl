---
title: 'How to: Cache data in a password-protected document (Jak buforować dane w dokumencie chronionym hasłem)'
description: Dowiedz się, że jeśli dodasz dane do pamięci podręcznej danych w dokumencie lub skoroszycie chronionym hasłem, możesz zapisać zmiany w danych w pamięci podręcznej, przesłaniając dwie metody w projekcie.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ccdb906022d4dcfc321af294eec59afa36832773
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824188"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>How to: Cache data in a password-protected document (Jak buforować dane w dokumencie chronionym hasłem)
  Jeśli dodasz dane do pamięci podręcznej danych w dokumencie lub skoroszycie chronionym hasłem, zmiany w buforowanych danych nie będą zapisywane automatycznie. Zmiany w buforowanych danych można zapisać, przesłaniając dwie metody w projekcie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Buforowanie w dokumentach programu Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Aby buforować dane w dokumencie programu Word chronionym hasłem

1. W klasie oznacz pole publiczne lub właściwość do `ThisDocument` buforowania. Aby uzyskać więcej informacji, zobacz [Cache data (Dane pamięci podręcznej).](../vsto/caching-data.md)

2. Zastąp <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodę w `ThisDocument` klasie i usuń ochronę z dokumentu.

     Po zapisaniu dokumentu metoda wywołuje tę metodę, aby można było wyłączyć [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ochronę dokumentu. Dzięki temu zmiany mają być zapisywane dane buforowane.

3. Zastąp <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodę w `ThisDocument` klasie i ponownie zastosuj ochronę dokumentu.

     Po zapisaniu dokumentu metoda wywołuje tę metodę, aby zapewnić możliwość ponownego ochrony [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dokumentu.

### <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak buforować dane w dokumencie programu Word, który jest chroniony hasłem. Zanim kod usunie ochronę w metodzie, zapisuje bieżącą wartość, aby można było ponownie użyć tego samego typu ochrony <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> w metodzie <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb" id="Snippet1":::

### <a name="compile-the-code"></a>Kompilowanie kodu
 Dodaj ten kod do `ThisDocument` klasy w projekcie. W tym kodzie założono, że hasło jest przechowywane w polu o nazwie `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Pamięć podręczna w skoroszytach programu Excel
 W projektach programu Excel ta procedura jest niezbędna tylko w przypadku ochrony całego skoroszytu hasłem przy użyciu <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metody . Ta procedura nie jest konieczna, jeśli za pomocą metody chronisz tylko określony arkusz przy użyciu <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> hasła.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Aby buforować dane w skoroszycie programu Excel chronionym hasłem

1. W klasie lub jednej z n klas oznacz pole publiczne lub właściwość do `ThisWorkbook` `Sheet`  buforowania. Aby uzyskać więcej informacji, zobacz [Dane pamięci podręcznej](../vsto/caching-data.md).

2. Zastąp <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodę w `ThisWorkbook` klasie i usuń ochronę ze skoroszytu.

     Po zapisaniu skoroszytu metoda wywołuje tę metodę, aby można było wyłączyć [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ochronę skoroszytu. Dzięki temu zmiany mają być zapisywane dane buforowane.

3. Zastąp <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodę w `ThisWorkbook` klasie i ponownie zastosuj ochronę dokumentu.

     Po zapisaniu skoroszytu metoda wywołuje tę metodę, aby zapewnić możliwość ponownego ochrony [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] skoroszytu.

### <a name="example"></a>Przykład
 Poniższy przykład kodu przedstawia sposób buforowania danych w skoroszycie programu Excel, który jest chroniony hasłem. Zanim kod usunie ochronę w metodzie, zapisuje bieżące wartości i , aby można było ponownie użyć tego samego typu ochrony w <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> metodzie <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs" id="Snippet1":::

### <a name="compile-the-code"></a>Kompilowanie kodu
 Dodaj ten kod do `ThisWorkbook` klasy w projekcie. W tym kodzie założono, że hasło jest przechowywane w polu o nazwie `securelyStoredPassword` .

## <a name="see-also"></a>Zobacz też
- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Jak buforować dane do użytku w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Jak programowo buforować źródło danych w dokumencie pakietu Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
