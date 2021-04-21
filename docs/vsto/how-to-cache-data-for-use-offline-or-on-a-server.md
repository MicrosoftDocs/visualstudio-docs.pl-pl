---
title: Jak buforować dane do użycia w trybie offline lub na serwerze
description: Oznacz element danych do buforowania w dokumencie, aby był dostępny w trybie offline. Dzięki temu dane w dokumencie mogą być manipulowane przez inny kod.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 07d7a33d90fd9d05c041ddc27f92a5b6a59bb75e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825995"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Jak buforować dane do użycia w trybie offline lub na serwerze
  Możesz oznaczyć element danych do buforowania w dokumencie, aby był dostępny w trybie offline. Umożliwia to również manipulowanie danymi w dokumencie za pomocą innego kodu, gdy dokument jest przechowywany na serwerze.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Możesz oznaczyć element danych do buforowania, gdy element danych jest zadeklarowany w kodzie, lub, jeśli używasz elementu , ustawiając właściwość w <xref:System.Data.DataSet> **oknie** Właściwości. Jeśli buforowany jest element danych, który nie jest elementem ani , upewnij się, że spełnia kryteria buforowania <xref:System.Data.DataSet> <xref:System.Data.DataTable> w dokumencie. Aby uzyskać więcej informacji, zobacz [Cache data (Dane pamięci podręcznej).](../vsto/caching-data.md)

> [!NOTE]
> Zestawy danych utworzone przy użyciu  usługi Visual Basic oznaczone jako Buforowane i **WithEvents** (w  tym zestawy danych przeciągane z okna źródeł danych lub przybornika z właściwością **CacheInDocument** ustawioną na **True)** mają znak podkreślenia poprzedzony ich nazwami w pamięci podręcznej.  Jeśli na przykład utworzysz zestaw danych i nadasz nazwę **Customers,** nazwa będzie _Customers <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> w pamięci podręcznej.  Jeśli używasz elementu w celu uzyskania dostępu do tego buforowanej pozycji, musisz określić wartość <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> **_Customers** zamiast **Customers**.

### <a name="to-cache-data-in-the-document-using-code"></a>Aby buforować dane w dokumencie przy użyciu kodu

1. Zadeklaruj pole publiczne lub właściwość elementu danych jako element członkowski klasy elementu hosta w projekcie, takiej jak klasa t w projekcie programu Word lub klasa `ThisDocumen` `ThisWorkbook` w projekcie programu Excel.

2. Zastosuj atrybut do elementu członkowskiego, aby oznaczyć element danych, który ma być przechowywany w pamięci <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> podręcznej danych dokumentu. W poniższym przykładzie ten atrybut jest stosowana do deklaracji pola dla <xref:System.Data.DataSet> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet11":::

3. Dodaj kod, aby utworzyć wystąpienie elementu danych i, jeśli ma to zastosowanie, załadować go z bazy danych.

     Element danych jest ładowany tylko podczas jego tworzenia po raz pierwszy; następnie pamięć podręczna pozostaje z dokumentem i należy napisać inny kod, aby go zaktualizować.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Aby buforować zestaw danych w dokumencie przy użyciu okno Właściwości

1. Dodaj zestaw danych do projektu przy użyciu narzędzi w Visual Studio, na przykład dodając źródło danych do projektu przy użyciu **okna Źródła** danych.

2. Utwórz wystąpienie zestawu danych, jeśli jeszcze go nie masz, i wybierz wystąpienie w projektancie.

3. W **oknie Właściwości** ustaw właściwość **CacheInDocument na** **wartość True.**

     Aby uzyskać więcej informacji, zobacz [Właściwości w projektach pakietu Office.](../vsto/properties-in-office-projects.md)

4. W **oknie** Właściwości ustaw właściwość **Modyfikatory** na **Wartość publiczna** (domyślnie jest to **Wartość wewnętrzna**).

## <a name="see-also"></a>Zobacz też
- [Dane pamięci podręcznej](../vsto/caching-data.md)
- [Jak programowo buforować źródło danych w dokumencie pakietu Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [How to: Cache data in a password-protected document (Jak buforować dane w dokumencie chronionym hasłem)](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md)
- [Zapisywanie danych](../data-tools/save-data-back-to-the-database.md)
