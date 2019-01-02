---
title: 'Instrukcje: Dane z pamięci podręcznej do użytku w trybie offline lub na serwerze'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b72748a4f37aa89fd12ba8751800fa9cb3c7be84
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939427"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Instrukcje: Dane z pamięci podręcznej do użytku w trybie offline lub na serwerze
  Można oznaczyć elementu danych w pamięci podręcznej w dokumencie, więc, że jest on dostępny w trybie offline. To również umożliwia dla danych w dokumencie, aby być manipulowane przez inny kod, gdy dokument jest przechowywany na serwerze.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Można oznaczyć elementu danych, można buforować, gdy element danych jest zadeklarowana w kodzie lub, jeśli używasz <xref:System.Data.DataSet>, ustawiając właściwość w **właściwości** okna. Jeśli są buforowanie elementu danych, który nie jest <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>, upewnij się, że spełnia kryteria są buforowane w dokumencie. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).

> [!NOTE]
>  Zestawy danych utworzone za pomocą Visual Basic, które są oznaczone jako **pamięci podręcznej** i **WithEvents** (w tym zestawy danych, które są przeciągnięte z **źródeł danych** okna lub **Przybornika** , które mają **CacheInDocument** właściwością **True**) ma znaku podkreślenia z poprzedzone ich nazwy w pamięci podręcznej. Na przykład, jeśli utworzysz zestaw danych i nadaj mu nazwę **klientów**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nazwa będzie **_Customers** w pamięci podręcznej. Kiedy używasz <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Aby uzyskać dostęp do tego elementu w pamięci podręcznej, należy określić **_Customers** zamiast **klientów**.

### <a name="to-cache-data-in-the-document-using-code"></a>Do buforowania danych w dokumencie przy użyciu kodu

1.  Zadeklaruj publiczne pole lub właściwość elementu danych jako składową klasy elementu hosta w projekcie, takie jak `ThisDocumen`t klasy w projekcie programu Word lub `ThisWorkbook` klasy w projekcie programu Excel.

2.  Zastosuj <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu do elementu członkowskiego, aby oznaczyć element danych, które mają być przechowywane w pamięci podręcznej danych dokumentu. Poniższy przykład dotyczy deklarację pola dla tego atrybutu <xref:System.Data.DataSet>.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3.  Dodaj kod, aby utworzyć wystąpienia elementu danych i, jeśli to konieczne, można go załadować z bazy danych.

     Element danych tylko jest ładowany podczas jej pierwszego tworzenia; Dzięki temu pamięci podręcznej pozostaje w dokumencie i trzeba napisać inny kod, aby go zaktualizować.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>W pamięci podręcznej zestawu danych w dokumencie za pomocą okna właściwości

1.  Dodaj zestaw danych do projektu przy użyciu narzędzi w Projektancie Visual Studio, na przykład poprzez dodanie źródła danych do projektu przy użyciu **źródeł danych** okna.

2.  Utwórz wystąpienie zestawu danych, jeśli jeszcze nie masz i wybierz wystąpienie w projektancie.

3.  W **właściwości** oknie **CacheInDocument** właściwości **True**.

     Aby uzyskać więcej informacji, zobacz [Properties in Office Projects](../vsto/properties-in-office-projects.md).

4.  W **właściwości** oknie **Modyfikatory** właściwości **publicznych** (domyślnie jest **wewnętrzne**).

## <a name="see-also"></a>Zobacz także
 [Dane z pamięci podręcznej](../vsto/caching-data.md) [jak: Programowe buforowanie źródła danych w dokumencie programu Word](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md) [jak: Buforowanie danych w dokumentach zabezpieczonych hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md) [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md) [zapisywanie danych](../data-tools/saving-data.md)
