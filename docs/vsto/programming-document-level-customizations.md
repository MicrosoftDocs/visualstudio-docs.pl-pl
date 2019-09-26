---
title: Dostosowywanie na poziomie dokumentu programu
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d1908f72bce01956bbb2eeb62bb9bbc30a64b0d
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254021"
---
# <a name="program-document-level-customizations"></a>Dostosowywanie na poziomie dokumentu programu
  Rozszerzając Microsoft Office Word lub Microsoft Office Excel przy użyciu dostosowania na poziomie dokumentu, można wykonać następujące zadania:

- Automatyzuj aplikację przy użyciu modelu obiektów.

- Dodaj kontrolki do powierzchni dokumentu.

- Wywołaj kod Visual Basic for Applications (VBA) w dokumencie z zestawu dostosowywania.

- Wywoływanie kodu w zestawie dostosowywania z poziomu języka VBA.

- Zarządzaj pewnymi aspektami dokumentu, gdy znajduje się on na serwerze, na którym nie zainstalowano Microsoft Office.

- Dostosuj interfejs użytkownika aplikacji.

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Niektóre aspekty pisania kodu w projektach na poziomie dokumentu różnią się od innych typów projektów w programie Visual Studio. Wiele z tych różnic jest spowodowanych sposobem, w jaki modele obiektów pakietu Office są uwidocznione w kodzie zarządzanym. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

  Aby uzyskać ogólne informacje na temat dostosowań na poziomie dokumentu i innych typów rozwiązań, które można utworzyć przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, zobacz temat [programowanie rozwiązań pakietu Office — omówienie &#40;programu VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-generated-classes-in-document-level-projects"></a>Korzystanie z wygenerowanych klas w projektach na poziomie dokumentu
 Podczas tworzenia projektu na poziomie dokumentu program Visual Studio automatycznie generuje klasę w projekcie, za pomocą której można zacząć pisać kod. Program Visual Studio generuje różne klasy dla programów Word i Excel:

- W projektach na poziomie dokumentu dla programu Word Klasa jest wywoływana `ThisDocument` domyślnie.

- Projekty na poziomie dokumentu dla programu Excel mają wiele wygenerowanych klas: jeden dla samego skoroszytu i jeden dla każdego arkusza. Domyślnie te klasy mają następujące nazwy:

  - `ThisWorkbook`

  - `Sheet1`

  - `Sheet2`

  - `Sheet3`

  Wygenerowana Klasa obejmuje programy obsługi zdarzeń, które są wywoływane, gdy dokument jest otwarty lub zamknięty. Aby uruchomić kod, gdy dokument jest otwarty, Dodaj kod do `Startup` programu obsługi zdarzeń. Aby uruchomić kod tuż przed zamknięciem dokumentu, Dodaj kod do `Shutdown` programu obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="understand-the-design-of-the-generated-classes"></a>Zrozumienie projektu wygenerowanych klas
 W projektach, które [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] są przeznaczone dla [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]lub, typy elementów hosta w interfejsach są, więc wygenerowane klasy nie mogą pochodzić od nich ich implementacji. Zamiast tego wygenerowane klasy uzyskują większość członków z następujących klas bazowych:

- `ThisDocument`: pochodzi od <xref:Microsoft.Office.Tools.Word.DocumentBase>.

- `ThisWorkbook`: pochodzi od <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.

- `Sheet`*n*: pochodzi od <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.

  Te klasy bazowe przekierowują wszystkie wywołania do ich członków do wewnętrznych implementacji odpowiednich interfejsów elementów hosta w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Na przykład w przypadku wywołania <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> metody `ThisDocument` klasy <xref:Microsoft.Office.Tools.Word.DocumentBase> Klasa przekierowuje <xref:Microsoft.Office.Tools.Word.Document> to wywołanie do wewnętrznej implementacji interfejsu w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="access-the-object-model-of-the-host-application"></a>Dostęp do modelu obiektów aplikacji hosta
 Aby uzyskać dostęp do modelu obiektów aplikacji hosta, Użyj elementów członkowskich wygenerowanej klasy w projekcie. Każda z tych klas odnosi się do obiektu w modelu obiektów programu Excel lub Word i zawiera większość tych samych właściwości, metod i zdarzeń. Na przykład `ThisDocument` Klasa w projekcie na poziomie dokumentu dla programu Word zawiera większość elementów członkowskich, <xref:Microsoft.Office.Interop.Word.Document> co obiekt w modelu obiektów programu Word.

 Poniższy przykład kodu pokazuje, jak używać modelu obiektów programu Word do zapisywania dokumentu, który jest częścią dostosowania na poziomie dokumentu dla programu Word. Ten przykład jest przeznaczony do uruchamiania z `ThisDocument` klasy.

```vb
Me.Save()
```

```csharp
this.Save();
```

 Aby zrobić to samo z zewnątrz `ThisDocument` klasy, `Globals` Użyj obiektu, aby uzyskać dostęp `ThisDocument` do klasy. Na przykład można dodać ten kod do pliku kodu okienka akcji, jeśli chcesz dołączyć przycisk **Zapisz** w interfejsie użytkownika okienka Akcje.

```vb
Globals.ThisDocument.Save()
```

```csharp
Globals.ThisDocument.Save();
```

 <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.Save%2A> `Save` <xref:Microsoft.Office.Tools.Word.Document> Ponieważ Klasa uzyskuje większość członków z elementu hosta, Metoda wywoływana w tym kodzie jest w rzeczywistości metodą elementu hosta. `ThisDocument` Ta metoda odpowiada <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodzie <xref:Microsoft.Office.Interop.Word.Document> obiektu w modelu obiektów programu Word.

 Aby uzyskać więcej informacji o korzystaniu z modeli obiektów programu Word i programu Excel, zobacz temat Omówienie [modelu obiektów programu Word](../vsto/word-object-model-overview.md) i [model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md).

 Aby uzyskać więcej informacji na `Globals` temat obiektu, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="add-controls-to-documents"></a>Dodawanie formantów do dokumentów
 Aby dostosować interfejs użytkownika dokumentu, można dodać kontrolki Windows Forms lub *formanty hosta* do powierzchni dokumentu. Łącząc różne zestawy kontrolek i pisząc kod, można powiązać kontrolki z danymi, zbierać informacje od użytkownika i reagować na akcje użytkownika.

 Formanty hosta to klasy, które poszerzają niektóre obiekty w modelu obiektów programu Word i Excel. Na przykład <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolka hosta udostępnia wszystkie funkcje <xref:Microsoft.Office.Interop.Excel.ListObject> programu w programie Excel. Jednak kontrolka <xref:Microsoft.Office.Tools.Excel.ListObject> hosta ma także dodatkowe możliwości zdarzeń i powiązania danych.

 Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md) oraz [kontrolek Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="combine-vba-and-document-level-customizations"></a>Łączenie języka VBA i dostosowań na poziomie dokumentu
 W dokumencie, który jest częścią dostosowania na poziomie dokumentu, można użyć kodu VBA. Można wywołać kod VBA w dokumencie z zestawu dostosowania, a także skonfigurować projekt, aby umożliwić kod VBA w dokumencie, aby wywołać kod w zestawie dostosowywania.

 Aby uzyskać więcej informacji, zobacz [łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="manage-documents-on-a-server"></a>Zarządzanie dokumentami na serwerze
 Można zarządzać kilkoma różnymi aspektami dostosowań na poziomie dokumentu na serwerze, na którym nie zainstalowano Microsoft Office Word ani Microsoft Office programu Excel. Można na przykład uzyskać dostęp do danych i modyfikować je w pamięci podręcznej danych dokumentu. Możesz również zarządzać zestawem dostosowań skojarzonym z dokumentem. Na przykład można programowo usunąć zestaw z dokumentu, tak aby dokument nie był już uruchamiany kod lub można programowo dołączyć zestaw do dokumentu.

 Aby uzyskać więcej informacji, zobacz [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji Microsoft Office
 Interfejs użytkownika programu Word i program Excel można dostosować w następujący sposób przy użyciu dostosowywania na poziomie dokumentu:

- Dodaj formanty hosta lub Windows Forms formanty do powierzchni dokumentu.

   Aby uzyskać więcej informacji, zobacz [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md), [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)i [kontrolek Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Dodaj okienko akcje do dokumentu.

   Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

- Dodaj karty niestandardowe do wstążki.

   Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

- Dodawanie grup niestandardowych do wbudowanej karty na Wstążce.

   Aby uzyskać więcej informacji, zobacz [jak: Dostosuj kartę](../vsto/how-to-customize-a-built-in-tab.md)wbudowaną.

  Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika aplikacji Microsoft Office, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Pobierz rozszerzone obiekty z natywnych obiektów pakietu Office w dostosowaniach na poziomie dokumentu
 Wiele programów obsługi zdarzeń dla zdarzeń pakietu Office odbiera natywny obiekt pakietu Office, który reprezentuje skoroszyt, arkusz lub dokument, który spowodował zdarzenie. W niektórych przypadkach może być konieczne uruchomienie pewnego kodu tylko wtedy, gdy skoroszyt lub dokument w dostosowaniu na poziomie dokumentu wywołał zdarzenie. Na przykład w dostosowaniu na poziomie dokumentu dla programu Excel można uruchomić jakiś kod, gdy użytkownik aktywuje jeden z arkuszy w dostosowanym skoroszycie, ale nie gdy użytkownik aktywuje arkusz w innym skoroszycie, który ma być otwarty w tym samym czasie.

 Gdy masz natywny obiekt pakietu Office, możesz sprawdzić, czy ten obiekt został rozszerzony do *elementu hosta* lub *formantu hosta* w dostosowaniu na poziomie dokumentu. Elementy hosta i formanty hosta są typami udostępnianymi przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] program, które dodają funkcje do obiektów, które znajdują się natywnie w modelu obiektów programu Word lub Excel (nazywane *natywnymi obiektami pakietu Office*). Zbiorczo elementy hosta i formanty hosta są również nazywane *obiektami rozszerzonymi*. Aby uzyskać więcej informacji na temat elementów hosta i kontrolek hosta, zobacz temat [elementy hosta i formanty hosta](../vsto/host-items-and-host-controls-overview.md).

## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>Poznaj metody GetVstoObject i HasVstoObject
 Aby przetestować natywny obiekt pakietu Office, użyj `HasVstoObject` metod `GetVstoObject` i w projekcie:

- Użyj metody `HasVstoObject` , jeśli chcesz określić, czy natywny obiekt pakietu Office ma rozszerzony obiekt w dostosowaniu. Ta metoda zwraca **wartość true** , jeśli natywny obiekt pakietu Office ma rozszerzony obiekt, a w przeciwnym razie ma **wartość false** .

- Użyj metody `GetVstoObject` , jeśli chcesz uzyskać rozszerzony obiekt dla natywnego obiektu pakietu Office. Ta metoda zwraca <xref:Microsoft.Office.Tools.Excel.ListObject>obiekt, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>lub <xref:Microsoft.Office.Tools.Word.Document> , jeśli określony natywny obiekt pakietu Office ma jeden. W przeciwnym razie zwracawartość`GetVstoObject` null. Na przykład `GetVstoObject` Metoda <xref:Microsoft.Office.Tools.Word.Document> zwraca wartość, jeśli określona <xref:Microsoft.Office.Interop.Word.Document> jest obiektem źródłowym dokumentu w projekcie dokumentu programu Word.

  W projektach na poziomie dokumentu `GetVstoObject` nie można użyć metody, aby utworzyć nowy <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>lub <xref:Microsoft.Office.Tools.Word.Document> element hosta w czasie wykonywania. Tej metody można użyć tylko w celu uzyskania dostępu do istniejących elementów hosta, które są generowane w projekcie w czasie projektowania. Jeśli chcesz utworzyć nowe elementy hosta w czasie wykonywania, należy opracować projekt dodatku VSTO. Aby uzyskać więcej informacji, zobacz Ograniczenia programowe [elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) oraz [rozszerzenia dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>Korzystanie z metod GetVstoObject i HasVstoObject
 Aby `HasVstoObject` wywołać metodę i `GetVstoObject` , użyj `Globals.Factory.GetVstoObject` metody lub `Globals.Factory.HasVstoObject` , a następnie Przekaż natywny obiekt Word lub Excel (taki jak <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet>), który chcesz przetestować.

## <a name="see-also"></a>Zobacz także
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Łączenie języka VBA i dostosowań na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)
- [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
