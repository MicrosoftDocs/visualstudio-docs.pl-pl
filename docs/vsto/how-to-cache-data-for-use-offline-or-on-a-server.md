---
title: 'Instrukcje: dane z pamięci podręcznej do użycia w trybie offline lub na serwerze'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 551d27cf8d40f2e6e9c996b031fa6c4e0a233355
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189565"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Instrukcje: dane z pamięci podręcznej do użycia w trybie offline lub na serwerze
  Można oznaczyć element danych, który ma zostać zbuforowany w dokumencie, tak aby był dostępny w trybie offline. Pozwala to również na manipulowanie danymi w dokumencie przez inny kod, gdy dokument jest przechowywany na serwerze.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Można oznaczyć element danych do zbuforowania, gdy element danych jest zadeklarowany w kodzie, lub, jeśli używasz <xref:System.Data.DataSet>, ustawiając właściwość w oknie **Właściwości** . W przypadku buforowania elementu danych, który nie jest <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>, należy się upewnić, że spełnia on kryteria w pamięci podręcznej w dokumencie. Aby uzyskać więcej informacji, zobacz [cache Data](../vsto/caching-data.md).

> [!NOTE]
> Zestawy danych utworzone przy użyciu Visual Basic, które są oznaczone jako **buforowane** i **WithEvents** (w tym zestawy danych, które są przeciągane z okna **źródła danych** lub **Przybornik** , który ma właściwość **CacheInDocument** ustawioną na **wartość true.** ) mają podkreślenie poprzedzone nazwami w pamięci podręcznej. Na przykład w przypadku utworzenia zestawu danych i nazwy **klientów**it nazwa <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> będzie **_Customers** w pamięci podręcznej. W przypadku korzystania z <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> w celu uzyskania dostępu do tego elementu w pamięci podręcznej należy określić **_Customers** zamiast **klientów**.

### <a name="to-cache-data-in-the-document-using-code"></a>Aby buforować dane w dokumencie przy użyciu kodu

1. Zadeklaruj pole publiczne lub właściwość dla elementu danych jako element członkowski klasy elementu hosta w projekcie, taki jak Klasa `ThisDocumen`t w projekcie programu Word lub Klasa `ThisWorkbook` w projekcie programu Excel.

2. Zastosuj atrybut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> do elementu członkowskiego, aby oznaczyć element danych, który ma być przechowywany w pamięci podręcznej danych dokumentu. Poniższy przykład stosuje ten atrybut do deklaracji pola dla <xref:System.Data.DataSet>.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. Dodaj kod, aby utworzyć wystąpienie elementu danych i, jeśli ma to zastosowanie, załadować go z bazy danych.

     Element danych jest ładowany dopiero po jego utworzeniu. następnie pamięć podręczna pozostaje w dokumencie i należy napisać inny kod, aby go zaktualizować.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Aby buforować zestaw danych w dokumencie przy użyciu okno Właściwości

1. Dodaj zestaw danych do projektu za pomocą narzędzi w projektancie programu Visual Studio, na przykład przez dodanie źródła danych do projektu przy użyciu okna **źródła danych** .

2. Utwórz wystąpienie zestawu danych, jeśli jeszcze go nie masz, i wybierz wystąpienie w projektancie.

3. W oknie **Właściwości** ustaw właściwość **CacheInDocument** na **wartość true**.

     Aby uzyskać więcej informacji, zobacz [właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md).

4. W oknie **Właściwości** ustaw właściwość **Modyfikatory** na **Public** (domyślnie jest to wartość **wewnętrzna**).

## <a name="see-also"></a>Zobacz także
- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Instrukcje: programowane buforowanie źródła danych w dokumencie pakietu Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Instrukcje: buforowanie danych w dokumencie chronionym hasłem](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)
- [Zapisz dane](../data-tools/save-data-back-to-the-database.md)
