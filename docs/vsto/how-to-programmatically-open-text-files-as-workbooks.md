---
title: 'How to: Programowe otwieranie plików tekstowych jako skoroszytów'
description: Dowiedz się, jak za pomocą Visual Studio programowo otworzyć plik tekstowy jako skoroszyt programu Microsoft Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14a73d7a06c3d79c15df5b823b38efc9ddceb846
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824175"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>How to: Programowe otwieranie plików tekstowych jako skoroszytów
  Plik tekstowy można otworzyć jako skoroszyt. Należy przekazać nazwę pliku tekstowego, który chcesz otworzyć. Można określić kilka parametrów opcjonalnych, takich jak numer wiersza, na którym ma być rozpoczynana analizowanie, oraz format kolumn danych w pliku.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet80":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet80":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład wymaga następujących składników:

- Rozdzielany przecinkami plik tekstowy o nazwie `Test.txt` zawierający co najmniej trzy wiersze tekstu.

- Plik `Test.txt` tekstowy, który ma być przechowywany na dysku C.

## <a name="see-also"></a>Zobacz też
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [How to: Programmatically open workbooks (2017: Programowe otwieranie skoroszytów)](../vsto/how-to-programmatically-open-workbooks.md)
- [Tworzyć programowo nowe skoroszyty](../vsto/how-to-programmatically-create-new-workbooks.md)
- [How to: Programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)
- [How to: Programmatically close workbooks (2017: Programowe zamykanie skoroszytów)](../vsto/how-to-programmatically-close-workbooks.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
