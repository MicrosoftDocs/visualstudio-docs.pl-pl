---
title: 'Instrukcje: Programowe otwieranie plików tekstowych jako skoroszytu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b0e333cd8ebb76df964c52ee48f4bde07e90fbaf
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866207"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Instrukcje: Programowe otwieranie plików tekstowych jako skoroszytu
  Można otworzyć pliku tekstowego jako skoroszyt. Należy podać nazwę pliku tekstowego, który chcesz otworzyć. Można określić kilka opcjonalnych parametrów, takich jak numer wiersza, w jaki do analizowania na początku i format kolumn danych w pliku.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 W tym przykładzie wymaga następujących składników:  
  
-   Tekst rozdzielany przecinkami plik o nazwie `Test.txt` zawierający co najmniej trzy wiersze tekstu.  
  
-   Plik tekstowy `Test.txt` mają być przechowywane na dysku C.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca ze skoroszytami](../vsto/working-with-workbooks.md)   
 [Instrukcje: Programowe otwieranie skoroszytów](../vsto/how-to-programmatically-open-workbooks.md)   
 [Instrukcje: Programowe tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Instrukcje: Programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)   
 [Instrukcje: Programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
