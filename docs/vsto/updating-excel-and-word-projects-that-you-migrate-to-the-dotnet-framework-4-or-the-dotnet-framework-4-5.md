---
title: Aktualizuj projekt programu Excel lub Word migrowany do .NET Framework 4/4,5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bc211f4d30359c885b22a45910363bbadca236f
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253719"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizowanie projektów programów Excel i Word, które są migrowane do .NET Framework 4 lub .NET Framework 4,5
  Jeśli masz projekt programu Excel lub Word, który używa dowolnej z następujących funkcji, musisz zmodyfikować kod, jeśli struktura docelowa zostanie zmieniona na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później:

- [Metody GetVstoObject i HasVstoObject](#GetVstoObject)

- [Wygenerowane klasy w projektach na poziomie dokumentu](#generatedclasses)

- [Kontrolki Windows Forms w dokumentach](#winforms)

- [Zdarzenia kontroli zawartości programu Word](#ccevents)

- [Klasy OLEObject i OLEControl](#ole)

- [Controls. Item (Object) — Właściwość](#itemproperty)

- [Kolekcje pochodne od CollectionBase](#collections)

  Należy również usunąć `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` odwołania i `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` do klasy z projektów programu Excel, które są przekierowywane do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub do nowszej wersji. Program Visual Studio nie usuwa tego atrybutu ani odwołania do klasy.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Usuń atrybut ExcelLocale1033 z projektów programu Excel
 Program został usunięty z części programu Visual Studio 2010 Tools for Office Runtime, który jest używany w rozwiązaniach [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] przeznaczonych dla systemu lub nowszych. `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` Środowisko uruchomieniowe języka wspólnego (CLR) w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszych wersjach zawsze przekazuje identyfikator ustawień regionalnych 1033 do modelu obiektów programu Excel i nie można już używać tego atrybutu, aby wyłączyć to zachowanie. Aby uzyskać więcej informacji, zobacz [globalizacja i lokalizacja rozwiązań programu Excel](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>Aby usunąć ExcelLocale1033Attribute

1. Po otwarciu projektu w programie Visual Studio Otwórz **Eksplorator rozwiązań**.

2. W węźle **Właściwości** (dla C#) lub węzła **mój projekt** (dla Visual Basic) kliknij dwukrotnie plik kodu AssemblyInfo, aby otworzyć go w edytorze kodu.

    > [!NOTE]
    > W projektach Visual Basic należy kliknąć przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań** , aby wyświetlić plik kodu AssemblyInfo.

3. `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` Znajdź i usuń go z pliku lub Dodaj do niego komentarz.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Usuń odwołanie do klasy ExcelLocal1033Proxy
 Projekty, które zostały utworzone przy użyciu narzędzi Microsoft Visual Studio 2005 dla systemu Microsoft Office, tworzą wystąpienie <xref:Microsoft.Office.Interop.Excel.Application> obiektu programu Excel przy `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` użyciu klasy. Ta klasa została usunięta z części programu Visual Studio 2010 Tools for Office Runtime, która jest używana na potrzeby rozwiązań [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] przeznaczonych dla lub nowszych. W związku z tym należy usunąć lub dodać komentarz do wiersza kodu, który odwołuje się do tej klasy.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Aby usunąć odwołanie do klasy ExcelLocal1033Proxy

1. Otwórz projekt w programie Visual Studio, a następnie otwórz **Eksplorator rozwiązań**.

2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla *ThisAddIn.cs* (for C#) lub *ThisAddIn. vb* (dla Visual Basic), a następnie wybierz polecenie **Wyświetl kod**.

3. W edytorze kodu w `VSTO generated code` regionie Usuń lub Skomentuj następujący wiersz kodu.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="GetVstoObject"></a>Aktualizowanie kodu korzystającego z metod GetVstoObject i HasVstoObject
 W projektach `GetVstoObject` przeznaczonych dla .NET Framework 3,5 metody lub `HasVstoObject` są dostępne jako metody rozszerzające na jednym z następujących obiektów natywnych w projekcie: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, lub <xref:Microsoft.Office.Interop.Excel.ListObject>. Gdy wywołujesz te metody, nie musisz przekazać parametru. Poniższy przykład kodu demonstruje, jak używać metody GetVstoObject w dodatku VSTO programu Word, który jest przeznaczony dla .NET Framework 3,5.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych należy zmodyfikować kod, aby uzyskać dostęp do tych metod w jeden z następujących sposobów:

- Nadal możesz uzyskiwać dostęp do tych metod jako metody rozszerzające <xref:Microsoft.Office.Interop.Excel.Workbook>dla <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Word.Document>obiektów, <xref:Microsoft.Office.Interop.Excel.ListObject> , lub. Należy jednak teraz przekazać obiekt zwracany przez `Globals.Factory` właściwość do tych metod.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Możesz Alternatywnie uzyskać dostęp do tych metod na obiekcie, który jest zwracany przez `Globals.Factory` właściwość. Gdy uzyskujesz dostęp do tych metod w ten sposób, musisz przekazać obiekt macierzysty, który ma zostać rozbudowany do metody.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="generatedclasses"></a>Aktualizuj kod, który używa wystąpień wygenerowanych klas w projektach na poziomie dokumentu
 W projektach na poziomie dokumentu, które są przeznaczone dla .NET Framework 3,5, wygenerowane klasy w projektach pochodzą od następujących klas w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych, typy [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] z wymienione powyżej są interfejsami, a nie klasami. Wygenerowane klasy w projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później pochodzą od następujących nowych klas [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]w:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Jeśli kod w projekcie odwołuje się do wystąpienia jednej z wygenerowanych klas jako klasa bazowa, z której pochodzi, należy zmodyfikować kod.

  Na przykład w projekcie skoroszytu programu Excel, który jest przeznaczony dla .NET Framework 3,5, może istnieć metoda pomocnika, która wykonuje pewne prace w wystąpieniach wygenerowanych `Sheet` *n* klas w projekcie.

```vb
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)
    ' Do something to the worksheet object.
End Sub
```

```csharp
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)
{
    // Do something to the worksheet object.
}
```

 Jeśli przekierujesz projekt do programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego, musisz wprowadzić jedną z następujących zmian w kodzie:

- Zmodyfikuj dowolny kod, który wywołuje `DoSomethingToSheet` metodę, aby <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> przekazać Właściwość <xref:Microsoft.Office.Tools.Excel.WorksheetBase> obiektu w projekcie. Ta właściwość zwraca <xref:Microsoft.Office.Tools.Excel.Worksheet> obiekt.

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- <xref:Microsoft.Office.Tools.Excel.WorksheetBase> Zmodyfikuj parametr `DoSomethingToSheet` metody, aby oczekiwać obiektu.

    ```vb
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)
        ' Do something to the worksheet object.
    End Sub
    ```

    ```csharp
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)
    {
        // Do something to the worksheet object.
    }
    ```

## <a name="winforms"></a>Aktualizuj kod, który używa formantów Windows Forms w dokumentach
 Należy dodać instrukcję **using** (C#) lub **Import** ( <xref:Microsoft.Office.Tools.Excel> Visual Basic) dla przestrzeni nazw lub <xref:Microsoft.Office.Tools.Word> do górnej części dowolnego pliku kodu, który używa właściwości Controls, aby dodać kontrolki Windows Forms do dokumentu lub arkusza programowa.

 W projektach przeznaczonych dla .NET Framework 3,5 metody, które dodają Windows Forms kontrolki (takie jak `AddButton` Metoda), są zdefiniowane <xref:Microsoft.Office.Tools.Excel.ControlCollection> w klasach i <xref:Microsoft.Office.Tools.Word.ControlCollection> .

 W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych metodami są metody rozszerzające, które są dostępne we właściwości kontrolki. Aby użyć tych metod rozszerzających, plik kodu, w którym są używane metody, musi mieć <xref:Microsoft.Office.Tools.Excel> instrukcję **using** lub **Imports** dla przestrzeni <xref:Microsoft.Office.Tools.Word> nazw lub. Ta instrukcja jest generowana automatycznie w nowych projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] dla lub później. Jednakże ta instrukcja nie jest automatycznie dodawana w projektach, które są przeznaczone dla .NET Framework 3,5, więc należy ją dodać po przekierowaniu projektu.

 Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="ccevents"></a>Aktualizuj kod, który obsługuje zdarzenia kontroli zawartości programu Word
 W projektach przeznaczonych dla .NET Framework 3,5 zdarzenia formantów zawartości programu Word są obsługiwane przez delegata ogólnego <xref:System.EventHandler%601> . W projektach, które są [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] przeznaczone dla lub nowsze, te zdarzenia są obsługiwane przez innych delegatów.

 Poniższa tabela zawiera listę zdarzeń kontroli zawartości programu Word i delegatów skojarzonych z nimi w projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych.

|Zdarzenie|Delegat do użycia w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] projektach i nowszych|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="ole"></a>Aktualizowanie kodu korzystającego z klas OLEObject i OLEControl
 W projektach przeznaczonych dla .NET Framework 3,5 można dodawać niestandardowe kontrolki (takie jak Windows Forms kontrolki użytkownika) do dokumentu lub arkusza przy użyciu `Microsoft.Office.Tools.Excel.OLEObject` klas i. `Microsoft.Office.Tools.Word.OLEControl`

 W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych, te klasy zostały zastąpione <xref:Microsoft.Office.Tools.Excel.ControlSite> przez interfejsy i <xref:Microsoft.Office.Tools.Word.ControlSite> . Należy zmodyfikować kod odwołujący się `Microsoft.Office.Tools.Excel.OLEObject` do `Microsoft.Office.Tools.Word.OLEControl` i zamiast tego odwoływać <xref:Microsoft.Office.Tools.Word.ControlSite> <xref:Microsoft.Office.Tools.Excel.ControlSite> się do i. Oprócz nowych nazw te kontrolki działają tak samo, jak w przypadku projektów przeznaczonych dla .NET Framework 3,5.

 Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="itemproperty"></a>Aktualizowanie kodu korzystającego z właściwości Controls. Item (Object)
 W projektach przeznaczonych dla .NET Framework 3,5 można użyć właściwości Item (Object) obiektu Microsoft. Office. Tools. Word. Document. Controls lub `Microsoft.Office.Tools.Excel.Worksheet.Controls` kolekcji, aby określić, czy dokument lub arkusz ma określoną kontrolkę.

 W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych Właściwość Item (Object) została usunięta z tych kolekcji. Aby określić, czy dokument lub arkusz zawiera określony formant, zamiast tego użyj metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> Contains (System. Object) kolekcji lub. <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A>

 Aby uzyskać więcej informacji na temat kontrolek kolekcji dokumentów i arkuszy, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="collections"></a>Aktualizowanie kodu, który używa kolekcji pochodzących od CollectionBase
 W projektach, które są przeznaczone dla .NET Framework 3,5, kilka typów kolekcji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] w <xref:System.Collections.CollectionBase> klasie pochodnej z klasy, `Microsoft.Office.Tools.SmartTagCollection`takiej `Microsoft.Office.Tools.Excel.ControlCollection`jak, `Microsoft.Office.Tools.Word.ControlCollection`, i.

 W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych te typy kolekcji są teraz interfejsami, które nie pochodzą od <xref:System.Collections.CollectionBase>. Niektóre elementy członkowskie nie są już dostępne w tych typach kolekcji, takich <xref:System.Collections.CollectionBase.Capacity%2A>jak <xref:System.Collections.CollectionBase.List%2A>,, <xref:System.Collections.CollectionBase.InnerList%2A>i.

## <a name="see-also"></a>Zobacz także
- [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Kontrolki zawartości](../vsto/content-controls.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
