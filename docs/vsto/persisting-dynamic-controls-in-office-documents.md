---
title: Utrwalanie formantów dynamicznych w dokumentach pakietu Office
description: Dowiedz się, w jaki sposób można dodać kod do rozwiązania, aby ponownie utworzyć trwałe dynamiczne kontrolki, gdy użytkownik ponownie otworzy zamknięty dokument.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e833a480713e3c04215c03a3dc4a549c92e0f772
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938476"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Utrwalanie formantów dynamicznych w dokumentach pakietu Office

Kontrolki dodawane w czasie wykonywania nie są utrwalane, gdy dokument lub skoroszyt jest zapisywany i zamykany. Dokładne zachowanie jest różne w przypadku formantów hosta i formantów Windows Forms. W obu przypadkach można dodać kod do rozwiązania, aby ponownie utworzyć kontrolki po ponownym otwarciu dokumentu przez użytkownika.

Kontrolki dodawane do dokumentów w czasie wykonywania są nazywane *kontrolkami dynamicznymi*. Aby uzyskać więcej informacji na temat formantów dynamicznych, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Utrwalanie formantów hosta w dokumencie

Po zapisaniu i zamknięciu dokumentu wszystkie dynamiczne kontrolki hosta są usuwane z dokumentu. Tylko bazowe natywne obiekty pakietu Office pozostają w tle. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> kontrolka hosta zmieni się na <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> . Natywne obiekty pakietu Office nie są połączone ze zdarzeniami kontroli hosta i nie mają funkcji powiązania danych formantu hosta.

Poniższa tabela zawiera listę natywnych obiektów pakietu Office, które są pozostawione w dokumencie dla każdego typu formantu hosta.

|Typ formantu hosta|Typ natywnego obiektu pakietu Office|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Ponownie utwórz dynamiczne kontrolki hosta podczas otwierania dokumentów

Możesz ponownie utworzyć dynamiczne kontrolki hosta zamiast istniejących formantów natywnych za każdym razem, gdy użytkownik otworzy dokument. Tworzenie kontrolek hosta w ten sposób, gdy dokument zostanie otwarty, symuluje środowisko, którego mogą oczekiwać użytkownicy.

Aby ponownie utworzyć formant hosta dla programu Word lub <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki hosta dla programu Excel, użyj `Add` \<*control class*> metody <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> lub <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> obiektu. Użyj metody, która ma parametr dla natywnego obiektu pakietu Office.

Na przykład jeśli chcesz utworzyć <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> formant hosta z istniejącej natywnej <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> , gdy dokument zostanie otwarty, użyj <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> metody i przekaż istniejący <xref:Microsoft.Office.Interop.Excel.ListObject> . Poniższy przykład kodu ilustruje ten element w projekcie na poziomie dokumentu dla programu Excel. Kod odtwarza dynamiczny <xref:Microsoft.Office.Tools.Excel.ListObject> , który jest oparty na istniejącym <xref:Microsoft.Office.Interop.Excel.ListObject> nazwie `MyListObject` w `Sheet1` klasie.

[!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
[!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]

### <a name="re-create-chart"></a>Utwórz ponownie wykres

Aby ponownie utworzyć <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> formant hosta, należy najpierw usunąć natywny <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> , a następnie ponownie utworzyć przy <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> użyciu <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> metody. Nie ma `Add` \<*control class*> metody, która umożliwia utworzenie nowego programu <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> opartego na istniejącym <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> .

Jeśli nie usuniesz najpierw natywnego, utworzysz <xref:Microsoft.Office.Interop.Excel.Chart> drugi, zduplikowany wykres po ponownym utworzeniu <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> .

## <a name="persist-windows-forms-controls-in-documents"></a>Utrwalaj Windows Forms kontrolki w dokumentach

Gdy dokument zostanie zapisany, a następnie zamknięty, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automatycznie usunie wszystkie dynamicznie utworzone kontrolki Windows Forms z dokumentu. Zachowanie jest jednak różne w przypadku projektów dodatków na poziomie dokumentu i narzędzi VSTO.

W przypadku dostosowań na poziomie dokumentu formanty i ich bazowe otoki ActiveX (które są używane do hostowania formantów w dokumencie) są usuwane przy następnym otwarciu dokumentu. Nie ma żadnego wskazania, że kontrolki były kiedykolwiek dostępne.

W dodatkach narzędzia VSTO formanty są usuwane, ale otoki ActiveX pozostają w dokumencie. Gdy użytkownik następnym razem otworzy dokument, otoki ActiveX są widoczne. W programie Excel otoki ActiveX wyświetlają obrazy formantów, jak pojawiły się podczas ostatniego zapisywania dokumentu. W programie Word otoki ActiveX są niewidoczne, chyba że użytkownik kliknie je, w takim przypadku wyświetla linię kropkowaną, która reprezentuje obramowanie kontrolek. Istnieje kilka sposobów usuwania otok ActiveX. Aby uzyskać więcej informacji, zobacz [usuwanie otoki ActiveX w dodatku](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Utwórz ponownie kontrolki Windows Forms, gdy dokumenty są otwarte

Po ponownym otwarciu dokumentu można utworzyć ponownie usunięte kontrolki Windows Forms. W tym celu Twoje rozwiązanie musi wykonać następujące zadania:

1. Przechowuj informacje o rozmiarze, lokalizacji i stanie formantów, gdy dokument jest zapisywany lub zamknięty. W dostosowaniu na poziomie dokumentu dane można zapisać w pamięci podręcznej danych w dokumencie. W dodatku VSTO można zapisać dane do niestandardowej części XML w dokumencie.

2. Ponownie utwórz kontrolki w zdarzeniu, które jest zgłaszane, gdy dokument zostanie otwarty. W projektach na poziomie dokumentu można to zrobić za pomocą `Sheet` *n* `_Startup` lub `ThisDocument_Startup` programów obsługi zdarzeń. W projektach dodatku VSTO można to zrobić w programach obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzeń lub.

### <a name="remove-activex-wrappers-in-an-add-in"></a><a name="removingActiveX"></a> Usuń otoki ActiveX w dodatku

Po dodaniu formantów Windows Forms dynamicznych do dokumentów przy użyciu dodatku VSTO można zapobiec wyświetlaniu przez niego otoki ActiveX w dokumencie przy następnym otwarciu w następujący sposób.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Usuń otoki ActiveX po otwarciu dokumentu

Aby usunąć wszystkie otoki ActiveX, wywołaj `GetVstoObject` metodę w celu wygenerowania elementu hosta dla <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Workbook> , który reprezentuje nowo otwarty dokument. Na przykład aby usunąć wszystkie otoki ActiveX z dokumentu programu Word, można wywołać `GetVstoObject` metodę w celu wygenerowania elementu hosta dla <xref:Microsoft.Office.Interop.Word.Document> obiektu, który jest przesyłany do programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzenia.

Ta procedura jest przydatna, gdy wiadomo, że dokument zostanie otwarty tylko na komputerach, na których zainstalowano dodatek VSTO. Jeśli dokument może zostać przesłany do innych użytkowników, którzy nie mają zainstalowanego dodatku VSTO, Rozważ usunięcie kontrolek przed zamknięciem dokumentu.

Poniższy przykład kodu demonstruje, jak wywołać metodę, `GetVstoObject` gdy dokument zostanie otwarty.

[!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
[!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]

Chociaż `GetVstoObject` Metoda jest używana głównie do generowania nowego elementu hosta w czasie wykonywania, ta metoda również czyści wszystkie otoki ActiveX z dokumentu przy pierwszym wywołaniu dla określonego dokumentu. Aby uzyskać więcej informacji o sposobach korzystania z `GetVstoObject` metody, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w DODATKach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

Jeśli Twój dodatek narzędzi VSTO tworzy dynamiczne kontrolki po otwarciu dokumentu, dodatek Narzędzia VSTO już wywoła `GetVstoObject` metodę jako część procesu, aby utworzyć formanty. Nie trzeba dodawać oddzielnego wywołania `GetVstoObject` metody, aby usunąć otoki ActiveX w tym scenariuszu.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Usuń formanty dynamiczne przed zamknięciem dokumentu

Dodatek VSTO może jawnie usunąć każdą dynamiczną kontrolę z dokumentu przed zamknięciem dokumentu. Ta procedura jest przydatna w przypadku dokumentów, które mogą być przesyłane do innych użytkowników, którzy nie mają zainstalowanego dodatku VSTO.

Poniższy przykład kodu demonstruje, jak usunąć wszystkie kontrolki Windows Forms z dokumentu programu Word, gdy dokument jest zamknięty.

[!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
[!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]

## <a name="see-also"></a>Zobacz też

- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
