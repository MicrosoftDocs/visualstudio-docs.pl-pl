---
title: 'How to: Programmatically save Visio documents (2017: Programowe zapisywanie dokumentów programu Visio)'
description: Dowiedz się, jak za pomocą Visual Studio programowo zapisywać istniejące dokumenty programu Microsoft Visio i nowe dokumenty, które nie zostały jeszcze zapisane.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 340d813a19c0c0dc5c347d3cfe4c7b29ff1bd049
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828998"
---
# <a name="how-to-programmatically-save-visio-documents"></a>How to: Programmatically save Visio documents (2017: Programowe zapisywanie dokumentów programu Visio)
  Istnieje kilka sposobów zapisywania dokumentów Microsoft Office Visio:

- Zapisz zmiany w istniejącym dokumencie.

- Zapisz nowy dokument lub zapisz go pod nową nazwą.

- Zapisz dokument z określonymi argumentami.

  Aby uzyskać więcej informacji, zobacz dokumentację referencyjną dotyczącąMicrosoft.Office.Interop.Visio.Doc[ VBA. Zapisz](/office/vba/api/Visio.Document.Save) [ metodę,Microsoft.Office.Interop.Visio.Document. Metoda SaveAs](/office/vba/api/Visio.Document.SaveAs) [ iMicrosoft.Office.Interop.Visio.Document. SaveAsEx,](/office/vba/api/Visio.Document.SaveAsEx) metoda.

## <a name="save-an-existing-document"></a>Zapisywanie istniejącego dokumentu

### <a name="to-save-a-document"></a>Aby zapisać dokument

- Wywołaj `Microsoft.Office.Interop.Visio.Document.Save` metodę `Microsoft.Office.Tools.Visio.Document` klasy dokumentu, która została wcześniej zapisana.

     Aby użyć tego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

    > [!NOTE]
    > Metoda `Microsoft.Office.Interop.Visio.Document.Save` zgłasza wyjątek, jeśli nowy dokument programu Visio nie został jeszcze zapisany.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet11":::

## <a name="save-a-document-with-a-new-name"></a>Zapisywanie dokumentu pod nową nazwą
 Użyj metody , aby zapisać nowy dokument lub dokument `Microsoft.Office.Interop.Visio.Document.SaveAs` o nowej nazwie. Ta metoda wymaga określenia nowej nazwy pliku.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Aby zapisać aktywny dokument programu Visio pod nową nazwą

- Wywołaj metodę metody , którą chcesz zapisać, używając w pełni `Microsoft.Office.Interop.Visio.Document.SaveAs` `Microsoft.Office.Tools.Visio.Document` kwalifikowanej ścieżki, w tym nazwy pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, zostanie dyskretnie zastąpiony.

     Aby użyć tego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet10":::

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Zapisywanie dokumentu z nową nazwą i określonymi argumentami
 Użyj metody `Microsoft.Office.Interop.Visio.Document.SaveAsEx` , aby zapisać dokument pod nową nazwą i określić wszelkie odpowiednie argumenty, które mają być stosowane do dokumentu.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Aby zapisać dokument z nową nazwą i określonymi argumentami

- Wywołaj metodę metody , którą chcesz zapisać, używając w pełni kwalifikowanej `Microsoft.Office.Interop.Visio.Document.SaveAsEx` `Microsoft.Office.Tools.Visio.Document` ścieżki, w tym nazwy pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, jest zgłaszany wyjątek.

     Poniższy przykład kodu zapisuje aktywny dokument pod nową nazwą, oznacza dokument jako tylko do odczytu i wyświetla dokument na liście ostatnio używanych dokumentów. Aby użyć tego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład kodu wymaga następujących czynności:

- Aby zapisać dokument o nowej nazwie, katalog o nazwie musi znajdować się w folderze Moje dokumenty (dla systemu Windows XP i starszych) lub w `Test` folderze *Dokumenty* (dla systemu Windows Vista). 

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)
- [How to: Programmatically create new Visio documents (Tworzyć programowo nowe dokumenty programu Visio)](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Jak programowo otwierać dokumenty programu Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Pisano: Programowe zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Jak programowo drukować dokumenty programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)
