---
title: 'Instrukcje: programowe zapisywanie dokumentów programu Visio'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 891a5c44159d10aacbb767cbc5376ae1d62252b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547059"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Instrukcje: programowe zapisywanie dokumentów programu Visio
  Istnieje kilka sposobów zapisywania Microsoft Office dokumentów programu Visio:

- Zapisz zmiany w istniejącym dokumencie.

- Zapisz nowy dokument lub Zapisz dokument z nową nazwą.

- Zapisz dokument z określonymi argumentami.

  Aby uzyskać więcej informacji, zobacz dokumentację referencyjną języka VBA dla [Microsoft.Office.Interop.Visio.Document. Metoda Save](/office/vba/api/Visio.Document.Save) [Microsoft.Office.Interop.Visio.Document. SaveAs](/office/vba/api/Visio.Document.SaveAs) i [Microsoft.Office.Interop.Visio.Document. SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) .

## <a name="save-an-existing-document"></a>Zapisz istniejący dokument

### <a name="to-save-a-document"></a>Aby zapisać dokument

- Wywołaj `Microsoft.Office.Interop.Visio.Document.Save` metodę `Microsoft.Office.Tools.Visio.Document` klasy dokumentu, który został wcześniej zapisany.

     Aby użyć tego przykładu kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

    > [!NOTE]
    > `Microsoft.Office.Interop.Visio.Document.Save`Metoda zgłasza wyjątek, jeśli nowy dokument programu Visio nie został jeszcze zapisany.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]

## <a name="save-a-document-with-a-new-name"></a>Zapisz dokument o nowej nazwie
 Użyj `Microsoft.Office.Interop.Visio.Document.SaveAs` metody do zapisania nowego dokumentu lub dokumentu o nowej nazwie. Ta metoda wymaga, aby określić nową nazwę pliku.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Aby zapisać aktywny dokument programu Visio przy użyciu nowej nazwy

- Wywołaj `Microsoft.Office.Interop.Visio.Document.SaveAs` metodę, `Microsoft.Office.Tools.Visio.Document` która ma zostać zapisana, przy użyciu w pełni kwalifikowanej ścieżki, w tym nazwy pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, zostanie nadpisany w trybie dyskretnym.

     Aby użyć tego przykładu kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Zapisz dokument z nową nazwą i określonymi argumentami
 Użyj `Microsoft.Office.Interop.Visio.Document.SaveAsEx` metody, aby zapisać dokument z nową nazwą, i określ odpowiednie argumenty, które mają być zastosowane do dokumentu.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Aby zapisać dokument z nową nazwą i określonymi argumentami

- Wywołaj `Microsoft.Office.Interop.Visio.Document.SaveAsEx` metodę, `Microsoft.Office.Tools.Visio.Document` która ma zostać zapisana, przy użyciu w pełni kwalifikowanej ścieżki, w tym nazwy pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, zgłaszany jest wyjątek.

     Poniższy przykład kodu zapisuje aktywny dokument przy użyciu nowej nazwy, oznacza dokument jako tylko do odczytu i pokazuje dokument z ostatnio używanej listy dokumentów. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład kodu wymaga następujących czynności:

- Aby zapisać dokument o nowej nazwie, katalog o nazwie musi znajdować się `Test` w folderze *Moje dokumenty* (dla systemu Windows XP i starszych) lub folderu *dokumenty* (dla systemu Windows Vista).

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Instrukcje: Programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Instrukcje: Programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Instrukcje: Programowane Zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Instrukcje: Programowane drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)
