---
title: 'Instrukcje: programowe otwieranie plików tekstowych jako skoroszytów'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 7a0f1b384aafb491183a750f17653ab55f2003e2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519836"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Instrukcje: programowe otwieranie plików tekstowych jako skoroszytów
  Plik tekstowy można otworzyć jako skoroszyt. Musisz przekazać nazwę pliku tekstowego, który chcesz otworzyć. Można określić kilka parametrów opcjonalnych, takich jak numer wiersza, od którego należy rozpocząć analizowanie, oraz format kolumny danych w pliku.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Przykład
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>Kompiluj kod
 W tym przykładzie wymagane są następujące składniki:

- Rozdzielany przecinkami plik tekstowy o nazwie zawierający `Test.txt` co najmniej trzy wiersze tekstu.

- Plik tekstowy, `Test.txt` który ma być przechowywany na dysku C.

## <a name="see-also"></a>Zobacz też
- [Pracuj ze skoroszytami](../vsto/working-with-workbooks.md)
- [Instrukcje: Programowane otwieranie skoroszytów](../vsto/how-to-programmatically-open-workbooks.md)
- [Instrukcje: Programowane tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Instrukcje: programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)
- [Instrukcje: programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
