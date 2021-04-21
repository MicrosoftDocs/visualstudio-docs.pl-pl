---
title: Rozszerzanie dokumentów programu Word & skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania
description: Dowiedz się, jak za pomocą dodatku VSTO dostosowywać dokumenty programu Word i skoroszyty programu Excel na różne sposoby.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 90dac328f336f7204bc9a70a0dbc543ec996922a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825670"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania
  Za pomocą dodatku VSTO można dostosować dokumenty programu Word i skoroszyty programu Excel w następujący sposób:

- Dodaj kontrolki zarządzane do dowolnego otwartego dokumentu lub arkusza.

- Przekonwertuj istniejący obiekt listy w arkuszu programu Excel na obiekt rozszerzony, który uwidacznia zdarzenia i może być powiązany z danymi przy <xref:Microsoft.Office.Tools.Excel.ListObject> użyciu Windows Forms powiązania danych.

- Uzyskiwanie dostępu do zdarzeń na poziomie aplikacji, które są udostępniane przez program Word i Excel dla określonych dokumentów, skoroszytów i arkuszy.

  Aby korzystać z tej funkcji, należy wygenerować obiekt w czasie działania, który rozszerza dokument lub skoroszyt.

  **Dotyczy:** Informacje zawarte w tym artykule dotyczą projektów dodatków VSTO dla następujących aplikacji: Excel i Word. Aby uzyskać więcej informacji, zobacz [Funkcje dostępne dla aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="generate-extended-objects-in-vsto-add-ins"></a>Generowanie obiektów rozszerzonych w dodatki VSTO
 *Obiekty rozszerzone* to wystąpienia typów udostępniane przez środowisko uruchomieniowe programu Visual Studio Tools for Office, które dodają funkcje do obiektów, które istnieją natywnie w modelach obiektów programu Word lub Excel (nazywanych natywnymi obiektami *pakietu Office).* Aby wygenerować obiekt rozszerzony dla obiektu programu Word lub Excel, użyj `GetVstoObject` metody . Przy pierwszym wywołaniu metody dla określonego obiektu programu Word lub Excel zwracany jest nowy obiekt, który `GetVstoObject` rozszerza określony obiekt. Za każdym razem, gdy wywołasz metodę i określisz ten sam obiekt programu Word lub Excel, zwraca ona ten sam obiekt rozszerzony.

 Typ obiektu rozszerzonego ma taką samą nazwę jak typ natywnego obiektu pakietu Office, ale typ jest zdefiniowany w przestrzeni <xref:Microsoft.Office.Tools.Excel> nazw <xref:Microsoft.Office.Tools.Word> lub . Jeśli na przykład wywołasz metodę `GetVstoObject` w celu rozszerzenia <xref:Microsoft.Office.Interop.Word.Document> obiektu, metoda zwróci obiekt <xref:Microsoft.Office.Tools.Word.Document> .

 Metody `GetVstoObject` są przeznaczone do głównie w projektach dodatków VSTO. Tych metod można również używać w projektach na poziomie dokumentu, ale zachowują się inaczej i mają mniej zastosowań.

 Aby określić, czy obiekt rozszerzony został już wygenerowany dla określonego natywnego obiektu pakietu Office, użyj `HasVstoObject` metody . Aby uzyskać więcej informacji, [zobacz Określanie, czy obiekt pakietu Office został rozszerzony.](#HasVstoObject)

### <a name="generate-host-items"></a>Generowanie elementów hosta
 W przypadku użycia obiektu na poziomie dokumentu (czyli obiektu , lub ) zwracany obiekt jest `GetVstoObject` <xref:Microsoft.Office.Interop.Excel.Workbook> nazywany <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Word.Document> *elementem hosta*. Element hosta to typ, który może zawierać inne obiekty, w tym inne rozszerzone obiekty i kontrolki. Przypomina odpowiedni typ w podstawowym zestawie międzyoptyku programu Word lub Excel, ale ma dodatkowe funkcje. Aby uzyskać więcej informacji na temat elementów hosta, zobacz [Host items and host controls overview (Elementy hosta i kontrolki hosta — omówienie).](../vsto/host-items-and-host-controls-overview.md)

 Po wygenerowaniu elementu hosta można go użyć do dodania zarządzanych kontrolek do dokumentu, skoroszytu lub arkusza. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek zarządzanych do dokumentów i arkuszy](#AddControls).

#### <a name="to-generate-a-host-item-for-a-word-document"></a>Aby wygenerować element hosta dla dokumentu programu Word

- W poniższym przykładzie kodu pokazano, jak wygenerować element hosta dla aktywnego dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet8":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet8":::

#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Aby wygenerować element hosta dla skoroszytu programu Excel

- Poniższy przykład kodu przedstawia sposób generowania elementu hosta dla aktywnego skoroszytu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs" id="Snippet2":::

#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Aby wygenerować element hosta dla arkusza programu Excel

- Poniższy przykład kodu przedstawia sposób generowania elementu hosta dla aktywnego arkusza w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs" id="Snippet1":::

### <a name="generate-listobject-host-controls"></a>Generowanie kontrolek hosta ListObject
 W przypadku użycia `GetVstoObject` metody do rozszerzenia metody metoda zwraca wartość <xref:Microsoft.Office.Interop.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> . Ma <xref:Microsoft.Office.Tools.Excel.ListObject> wszystkie funkcje oryginalnego <xref:Microsoft.Office.Interop.Excel.ListObject> . Ma ona również dodatkowe funkcje i może być powiązana z danymi przy użyciu Windows Forms modelu powiązania danych. Aby uzyskać więcej informacji, zobacz [ListObject, kontrolka](../vsto/listobject-control.md).

#### <a name="to-generate-a-host-control-for-a-listobject"></a>Aby wygenerować kontrolkę hosta dla listObject

- Poniższy przykład kodu pokazuje, jak wygenerować dla pierwszego w aktywnym <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Interop.Excel.ListObject> arkuszu w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs" id="Snippet3":::

### <a name="add-managed-controls-to-documents-and-worksheets"></a><a name="AddControls"></a> Dodawanie kontrolek zarządzanych do dokumentów i arkuszy
 Po wygenerowaniu obiektu lub można dodać do dokumentu lub arkusza kontrolki <xref:Microsoft.Office.Tools.Word.Document> reprezentowane przez te obiekty <xref:Microsoft.Office.Tools.Excel.Worksheet> rozszerzone. Aby dodać kontrolki, `Controls` użyj właściwości <xref:Microsoft.Office.Tools.Word.Document> lub <xref:Microsoft.Office.Tools.Excel.Worksheet> . Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 Możesz dodać kontrolki Windows Forms lub *formanty hosta.* Kontrolka hosta to kontrolka dostarczana przez kontrolkę, która opakowywuje odpowiednią kontrolkę w podstawowym zestawie międzyoptyku programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Word lub Excel. Kontrolka hosta uwidacznia całe zachowanie podstawowego natywnego obiektu pakietu Office. Zgłasza również zdarzenia i może być powiązany z danymi przy użyciu Windows Forms powiązania danych. Aby uzyskać więcej informacji, zobacz [Host items and host controls overview (Omówienie elementów hosta i kontrolek hosta).](../vsto/host-items-and-host-controls-overview.md)

> [!NOTE]
> Za pomocą dodatku VSTO nie można dodać kontrolki do arkusza ani kontrolki ani do <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Word.XMLNode> <xref:Microsoft.Office.Tools.Word.XMLNodes> dokumentu. Tych kontrolek hosta nie można dodać programowo. Aby uzyskać więcej informacji, zobacz [Programowe ograniczenia elementów hosta i kontrolek hosta.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

### <a name="persist-and-remove-controls"></a>Utrwalanie i usuwanie kontrolek
 Po dodaniu zarządzanych kontrolek do dokumentu lub arkusza kontrolki nie są utrwalane, gdy dokument jest zapisywany, a następnie zamykany. Wszystkie kontrolki hosta są usuwane, dzięki czemu zostaną pozostawione tylko podstawowe natywne obiekty pakietu Office. Na przykład , staje <xref:Microsoft.Office.Tools.Excel.ListObject> się . <xref:Microsoft.Office.Interop.Excel.ListObject> Wszystkie Windows Forms są również usuwane, ale otoki ActiveX dla kontrolek są pozostawiane w dokumencie. Musisz dołączyć kod do dodatku VSTO, aby wyczyścić kontrolki lub ponownie utworzyć kontrolki przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

## <a name="access-application-level-events-on-documents-and-workbooks"></a>Uzyskiwanie dostępu do zdarzeń na poziomie aplikacji w dokumentach i skoroszytach
 Niektóre zdarzenia dokumentów, skoroszytów i arkuszy w natywnych modelach obiektów programów Word i Excel są wywoływane tylko na poziomie aplikacji. Na przykład zdarzenie jest wywoływane, gdy dokument jest otwierany w programie Word, ale to zdarzenie jest definiowane w klasie <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> , a nie w klasie <xref:Microsoft.Office.Interop.Word.Application> <xref:Microsoft.Office.Interop.Word.Document> .

 W przypadku używania tylko natywnych obiektów pakietu Office w dodatku VSTO należy obsługiwać te zdarzenia na poziomie aplikacji, a następnie napisać dodatkowy kod, aby określić, czy dokument, który wywłaścił zdarzenie, jest tym, który został dostosowany. Elementy hosta zapewniają te zdarzenia na poziomie dokumentu, co ułatwia obsługę zdarzeń dla określonego dokumentu. Możesz wygenerować element hosta, a następnie obsłużyć zdarzenie dla tego elementu hosta.

### <a name="example-that-uses-native-word-objects"></a>Przykład, który używa natywnych obiektów programu Word
 Poniższy przykład kodu pokazuje, jak obsługiwać zdarzenie na poziomie aplikacji dla dokumentów programu Word. Metoda tworzy nowy dokument, a następnie definiuje program obsługi zdarzeń, `CreateDocument` <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> który uniemożliwia zapisanie tego dokumentu. Zdarzenie to zdarzenie na poziomie aplikacji, które jest wywoływane dla obiektu , a procedura obsługi zdarzeń musi porównać parametr z obiektem , aby określić, czy reprezentuje <xref:Microsoft.Office.Interop.Word.Application> `Doc` zapisany `document1` `document1` dokument.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet12":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet12":::

### <a name="examples-that-use-a-host-item"></a>Przykłady, które używają elementu hosta
 Poniższe przykłady kodu upraszczają ten proces przez obsługę <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> zdarzenia <xref:Microsoft.Office.Tools.Word.Document> elementu hosta. Metoda w tych przykładach generuje obiekt , który rozszerza obiekt , a następnie definiuje program obsługi zdarzeń, który uniemożliwia `CreateDocument2` <xref:Microsoft.Office.Tools.Word.Document> `document2` <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> zapisanie dokumentu. Program obsługi zdarzeń jest wywoływany tylko wtedy, gdy jest zapisywany, i może anulować akcję zapisywania bez wykonywania dodatkowej pracy w celu sprawdzenia, `document2` który dokument został zapisany.

 W poniższym przykładzie kodu przedstawiono to zadanie.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet13":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet13":::

## <a name="determine-whether-an-office-object-has-been-extended"></a><a name="HasVstoObject"></a> Określanie, czy obiekt pakietu Office został rozszerzony
 Aby określić, czy obiekt rozszerzony został już wygenerowany dla określonego natywnego obiektu pakietu Office, użyj `HasVstoObject` metody . Ta metoda zwraca **wartość true,** jeśli obiekt rozszerzony został już wygenerowany.

 Użyj metody `Globals.Factory.HasVstoMethod`. Przekaż natywny obiekt programu Word lub Excel, taki jak lub , który chcesz <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Excel.Worksheet> przetestować dla obiektu rozszerzonego.

 Metoda jest przydatna, gdy chcesz uruchamiać kod tylko wtedy, gdy określony obiekt `HasVstoObject` pakietu Office ma obiekt rozszerzony. Jeśli na przykład masz dodatek Word VSTO obsługujący zdarzenie w celu usunięcia zarządzanych kontrolek z dokumentu przed jego zapisaniem, użyj metody , aby określić, czy dokument <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> `HasVstoObject` został rozszerzony. Jeśli dokument nie został rozszerzony, nie może mieć kontrolek zarządzanych, a procedura obsługi zdarzeń może zwrócić bez próby oczyszczenia kontrolek w dokumencie.

## <a name="see-also"></a>Zobacz też
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Office development samples and walkthroughs (Przykłady i wskazówki dotyczące tworzenia aplikacji pakietu Office)](../vsto/office-development-samples-and-walkthroughs.md)
