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
ms.openlocfilehash: ed7698db0c235bb5c49379c4a6fb0312895f4b1a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866964"
---
# <a name="properties-in-office-projects"></a>Właściwości w projektach pakietu Office
  Istnieje kilka ważnych właściwości, które są dostępne dla projektów pakietu Office w Visual Studio. Te właściwości można uzyskiwać w **właściwości** okna.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="namespace-for-host-item"></a>Namespace dla elementu hosta  
 Użyj **Namespace dla elementu hosta** właściwości do zmiany przestrzeni nazw dla klas elementu hosta (na przykład `ThisAddIn`, `ThisWorkbook`, lub `ThisDocument` klasy) w elemencie wizualnym C# projektów. Właściwość ta pojawia się w **właściwości** okna po wybraniu węzła dokumentu w projekcie na poziomie dokumentu (takie jak *ExcelWorkbook1.xlsx* lub *WordDocument1.docx* ) lub węzła aplikacji w dodatku narzędzi VSTO dla programów w projekcie (np. Excel lub Word) w **Eksploratora rozwiązań**.  
  
 Po utworzeniu wizualizacji C# Office project elementów hosta są podane przestrzeni nazw na podstawie nazwy projektu. Zaleca się, że używasz **Namespace dla elementu hosta** właściwość Zmienianie przestrzeni nazw, a nie Edytuj kod bezpośrednio do plików. Gdy używasz tej właściwości, przestrzeń nazw jest zmieniany w plikach wygenerowanego kodu (ukryte), a także w widocznych plików kodu.  
  
## <a name="cacheindocument"></a>CacheInDocument  
 **CacheInDocument** właściwość pojawia się w **właściwości** okna dla projektów na poziomie dokumentu po wybraniu wystąpienia <xref:System.Data.DataSet> w Projektancie Visual Studio. Tylko publiczne składowe mogą być buforowane; Upewnij się, że **Modyfikatory** właściwość jest ustawiona na **publicznych** jeśli mają być buforowane <xref:System.Data.DataSet>.  
  
 Ta właściwość przyjmuje wartość logiczną:  
  
- Wybierz **true** w pamięci podręcznej zestawu danych w dokumencie.  
  
- Wybierz **false** Jeśli nie chcesz, aby zestaw danych w pamięci podręcznej w dokumencie.  
  
  Aby uzyskać więcej informacji na temat buforowania danych, zobacz [dane dostosowywane na poziomie dokumentu z pamięci podręcznej](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="value2"></a>Wartość2  
 **Wartość2** właściwość jest dostępna tylko dla projektów skoroszytem lub szablonem programu Excel. Wygląda na to, w obszarze **powiązania danych** właściwość węzła w **właściwości** okna po wybraniu <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu w Projektancie arkusza.  
  
 Użyj **wartość2** właściwość **właściwości** okna, aby powiązać <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwość <xref:Microsoft.Office.Tools.Excel.NamedRange> do pola w źródle danych.  
  
## <a name="see-also"></a>Zobacz także  
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)   
 [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)  
