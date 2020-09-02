---
title: Właściwości w projektach pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9fc2a0774206eac0c9295a425d81555ffdd3cac8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561376"
---
# <a name="properties-in-office-projects"></a>Właściwości w projektach pakietu Office
  Istnieje kilka ważnych właściwości, które są dostępne dla projektów pakietu Office w programie Visual Studio. Dostęp do tych właściwości można uzyskać w oknie **Właściwości** .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Przestrzeń nazw dla elementu hosta
 Użyj **przestrzeni nazw dla właściwości element hosta** , aby zmienić przestrzeń nazw dla klas elementów hosta (na przykład, `ThisAddIn` `ThisWorkbook` lub `ThisDocument` klasy) w projektach Visual C#. Ta właściwość pojawia się w oknie **Właściwości** , gdy wybierzesz węzeł dokumentu w projekcie na poziomie dokumentu (na przykład *ExcelWorkbook1.xlsx* lub *WordDocument1.docx*) lub węzeł aplikacji w projekcie dodatku VSTO (takim jak Excel lub Word) w **Eksplorator rozwiązań**.

 Podczas tworzenia projektu pakietu Office w języku Visual C# elementy hosta otrzymują przestrzeń nazw na podstawie nazwy projektu. Zaleca się użycie **przestrzeni nazw dla właściwości element hosta** , aby zmienić przestrzeń nazw, a nie bezpośrednio edytować pliki kodu. W przypadku użycia tej właściwości przestrzeń nazw jest zmieniana w wygenerowanych (ukrytych) plikach kodu, a także w plikach widocznej kodu.

## <a name="cacheindocument"></a>CacheInDocument
 Właściwość **CacheInDocument** pojawia się w oknie **Właściwości** dla projektów na poziomie dokumentu w przypadku wybrania wystąpienia obiektu <xref:System.Data.DataSet> w projektancie programu Visual Studio. Tylko publiczne elementy członkowskie mogą być buforowane; Upewnij się, że właściwość **Modyfikatory** jest ustawiona na wartość **Public** , jeśli chcesz buforować w pamięci podręcznej <xref:System.Data.DataSet> .

 Ta właściwość przyjmuje wartość logiczną:

- Wybierz **wartość true** , aby buforować zestaw danych w dokumencie.

- Wybierz **wartość FAŁSZ** , jeśli nie chcesz, aby zestaw danych był buforowany w dokumencie.

  Aby uzyskać więcej informacji na temat buforowania danych, zobacz [buforowane dane w obszarze dostosowania na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md).

## <a name="value2"></a>Wartość2
 Właściwość **wartość2** jest dostępna tylko dla skoroszytów programu Excel lub projektów szablonów. Jest ona wyświetlana w węźle właściwości **DataBindings** w oknie **Właściwości** po wybraniu <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w projektancie arkusza.

 Użyj właściwości **wartość2** w oknie **Właściwości** , aby powiązać właściwość z <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> do pola w źródle danych.

## <a name="see-also"></a>Zobacz też
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
- [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)
