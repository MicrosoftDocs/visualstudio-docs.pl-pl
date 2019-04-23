---
title: Model obiektu Wstążka ― omówienie
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5958eb6fb8fd14dd510fa87d900efa76cb6f6a87
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040719"
---
# <a name="ribbon-object-model-overview"></a>Model obiektu Wstążka ― omówienie
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Udostępnia model silnie typizowany obiekt, który służy do pobierania i ustawiania właściwości formantów wstążki w czasie wykonywania. Na przykład użytkownik może dynamicznie wypełnianie kontrolek menu lub wyświetlania i ukrywania kontrolek kontekstowe. Na Wstążce, ale tylko w przypadku, przed załadowaniem wstążki według aplikacji pakietu Office, można dodać karty, grupy i formanty. Aby uzyskać informacje, zobacz [Ustaw właściwości, które stają się tylko do odczytu](#SettingReadOnlyProperties).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Ten model obiektu Wstążka składa się przede wszystkim [wstążki klasy](#RibbonClass), [wstążki zdarzenia](#RibbonEvents), i [klasy kontrolek wstążki](#RibbonControlClasses).

## <a name="RibbonClass"></a> Klasa wstążki
 Po dodaniu nowego **Wstążka (Projektant graficzny)** elementu do projektu, program Visual Studio dodaje **wstążki** klasy do projektu. **Wstążki** klasa dziedziczy <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> klasy.

 Ta klasa jest wyświetlany jako częściowe klasy, który jest podzielony między plik kodu Wstążki i plik kodu projektanta wstążki.

## <a name="RibbonEvents"></a> Zdarzeń wstążki
 **Wstążki** klasa zawiera trzy następujące zdarzenia:

|Zdarzenie|Opis|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Wywoływane podczas ładowania dostosowania wstążki w aplikacji pakietu Office. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> Program obsługi zdarzeń jest automatycznie dodawany do pliku kodu wstążki. Użyj tej obsługi zdarzeń, aby uruchomić kod niestandardowy, po załadowaniu wstążki.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Włącza pamięć podręczną obrazów w dostosowaniu na Wstążce, po załadowaniu wstążki. Możesz uzyskać nieznaczne są bardziej wydajne, jeśli piszesz kod w pamięci podręcznej obrazów wstążki w tej obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Wywoływane, gdy zamyka wystąpienie wstążki.|

## <a name="RibbonControlClasses"></a> Formanty Wstążki
 <xref:Microsoft.Office.Tools.Ribbon> Przestrzeń nazw zawiera typ dla każdego formantu, który zostanie wyświetlony w **formanty wstążki Office** grupy **przybornika**.

 W poniższej tabeli przedstawiono typ dla każdego `Ribbon` kontroli. Aby uzyskać opis każdego formantu, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).

|Nazwa kontrolki|Nazwa klasy|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Przycisk**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**Grupa przycisków**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Galeria**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Grupa**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Etykieta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Karta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 <xref:Microsoft.Office.Tools.Ribbon> Przestrzeń nazw używa prefiksu "Wstążki" dla tych typów w celu uniknięcia kolizji nazw z nazwami klas kontroli w <xref:System.Windows.Forms> przestrzeni nazw.

 Gdy dodajesz formant do projektanta wstążki, Projektant wstążki deklaruje klasę dla tej kontrolki jako pole w plik kodu projektanta wstążki.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Typowe zadania za pomocą właściwości formantów wstążki
 Każdy `Ribbon` kontrolka zawiera właściwości, które służy do wykonywania różnych zadań, takich jak przypisanie etykiety do formantu, lub wyświetlanie i ukrywanie formantów.

 W niektórych przypadkach właściwości stają się tylko do odczytu po obciążeń Wstążki lub formant jest dodawany do menu dynamiczne. Aby uzyskać więcej informacji, zobacz [Ustaw właściwości, które stają się tylko do odczytu](#SettingReadOnlyProperties).

 W poniższej tabeli opisano niektóre zadania, które można wykonać przy użyciu `Ribbon` właściwości formantu.

|Dla tego zadania:|wykonaj następujące czynności:|
|--------------------|--------------|
|Ukryć lub pokazać kontrolki.|Użyj właściwości widoczne.|
|Włącz lub Wyłącz formant.|Użyj właściwości włączone.|
|Ustaw rozmiar kontrolki.|Użyj właściwości ControlSize.|
|Pobierz obraz, który widoczny na kontrolce.|Użyj właściwości obrazu.|
|Zmiana etykiety formantu.|Użyj właściwości etykiety.|
|Dodawanie danych zdefiniowane przez użytkownika do kontrolki.|Użyj właściwości Tag.|
|Pobierz elementy w <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, lub<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> formant.|Użyj właściwości Items.|
|Dodaj elementy do <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, lub <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> kontroli.|Użyj właściwości Items.|
|Dodawanie formantów do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Użyj właściwości Items.<br /><br /> Aby dodać formanty do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po załadowaniu wstążki do aplikacji pakietu Office, należy ustawić <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> właściwości **true** przed załadowaniem wstążki do aplikacji pakietu Office. Aby uzyskać informacje, zobacz [Ustaw właściwości, które stają się tylko do odczytu](#SettingReadOnlyProperties).|
|Pobieranie wybranego elementu <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, lub <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Użyj właściwości SelectedItem. Aby uzyskać <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> właściwości.|
|Pobieranie grup <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> właściwości.|
|Określ liczbę wierszy i kolumn, które pojawiają się w <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> i <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> właściwości.|

## <a name="SettingReadOnlyProperties"></a> Ustaw właściwości, które stają się tylko do odczytu
 Niektóre właściwości można ustawić tylko przed ładuje wstążki. Istnieją trzy miejsca, aby ustawić te właściwości:

- W programie Visual Studio **właściwości** okna.

- W Konstruktorze typu **wstążki** klasy.

- W `CreateRibbonExtensibilityObject` metody `ThisAddin`, `ThisWorkbook`, lub `ThisDocument` klasy projektu.

  Menu dynamiczne zawierają niektóre wyjątki. Możesz utworzyć nowe kontrolki, ustawiać ich właściwości i dodać je do menu dynamiczne w czasie wykonywania, nawet w przypadku, po załadowaniu wstążki, który zawiera menu.

  W dowolnym momencie można ustawić właściwości formantów, które dodajesz do menu dynamiczne.

  Aby uzyskać więcej informacji, zobacz [właściwości, które stają się tylko do odczytu](#ReadOnlyProperties).

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Ustawianie właściwości w Konstruktorze wstążki
 Można ustawić właściwości `Ribbon` kontroli w Konstruktorze typu **wstążki** klasy. Ten kod musi znajdować się po wywołaniu `InitializeComponent` metody. Poniższy przykład dodaje nowy przycisk do grupy, jeśli aktualna godzina jest 17:00 czasu pacyficznego (UTC-8) lub nowszej.

 Dodaj następujący kod.

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 W elemencie wizualnym C# projektów, które zostały uaktualnione z programu Visual Studio 2008, Konstruktor pojawia się w pliku kodu wstążki.

 W projektach języka Visual Basic lub Visual C# projektów, które zostały utworzone w [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], Konstruktor, który pojawia się w pliku kodu projektanta wstążki. Ten plik ma nazwę *YourRibbonItem*. Designer.cs narzędzie lub *YourRibbonItem*. Designer.VB. Aby wyświetlić ten plik w projektach języka Visual Basic, należy najpierw kliknąć **Pokaż wszystkie pliki** przycisku w Eksploratorze rozwiązań.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Ustawianie właściwości w metodzie CreateRibbonExtensibilityObject
 Można ustawić właściwości `Ribbon` kontroli, gdy zastąpisz `CreateRibbonExtensibilityObject` method in Class metoda `ThisAddin`, `ThisWorkbook`, lub `ThisDocument` klasy projektu. Aby uzyskać więcej informacji na temat `CreateRibbonExtensibilityObject` metody, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).

 Poniższy przykład ustawia właściwości wstążki w `CreateRibbonExtensibilityObject` metody `ThisWorkbook` klasy projektu skoroszytu programu Excel.

 Dodaj następujący kod.

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="ReadOnlyProperties"></a> Właściwości, które stają się tylko do odczytu
 W poniższej tabeli przedstawiono właściwości, które można ustawić tylko przed ładuje wstążki.

> [!NOTE]
>  W dowolnym momencie można ustawić właściwości kontrolek na menu dynamiczne. Ta tabela nie ma zastosowania w takiej sytuacji.

|Właściwość|Klasa formantów wstążki|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**columnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Vlastnosti ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dynamic**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Grupy**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Nazwa**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Stanowisko**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Liczba wierszy**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Karty**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Tytuł**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Ustawianie właściwości dla wstążek, które pojawiają się na inspektorów programu Outlook
 Nowe wystąpienie klasy wstążki jest tworzony każdorazowo użytkownik otwiera Inspektor pojawia się wstążki. Jednak można ustawić właściwości wymienionych w powyższej tabeli wyłącznie przed utworzeniem pierwszego wystąpienia wstążki. Po pierwszym utworzeniu wystąpienia, te właściwości staną się tylko do odczytu, ponieważ pierwsze wystąpienie określa plik XML, który korzysta z programu Outlook do załadowania na Wstążce.

 Jeśli masz logikę warunkową, która ustawia żadnej z tych właściwości na inną wartość, gdy tworzone są inne wystąpienia wstążki, ten kod odniesie żadnego skutku.

> [!NOTE]
>  Upewnij się, że **nazwa** właściwość jest ustawiona dla każdego formantu, który dodasz do Wstążki programu Outlook. Jeśli dodasz formant do Wstążki programu Outlook w czasie wykonywania, należy ustawić tę właściwość w kodzie. Jeśli dodasz formant do Wstążki programu Outlook w czasie projektowania, nazwa właściwości jest ustawiana automatycznie.

## <a name="ribbon-control-events"></a>Zdarzeń kontrolek wstążki
 Każda klasa formantu zawiera jeden lub więcej zdarzeń. W poniższej tabeli opisano te zdarzenia.

|Zdarzenie|Opis|
|-----------|-----------------|
|Kliknij|Występuje po kliknięciu formantu.|
|Textchanged.|Występuje po zmianie tekstu w polu edycji lub pola kombi.|
|ItemsLoading|Występuje, gdy kolekcja elementów kontrolki są wymagane przez pakiet Office. Office buforuje kolekcji elementów, dopóki kod ulegnie zmianie właściwości formantu lub wywołać <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> metody.|
|ButtonClick|Występuje, gdy przycisk w <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> lub <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> kliknięciu.|
|SelectionChanged|Występuje, gdy wybór w <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> lub <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> zmiany.|
|DialogLauncherClick|Występuje po kliknięciu ikony uruchamianie okna dialogowego, w prawym dolnym rogu grupy.|

 Programy obsługi zdarzeń dla zdarzenia te mają następujące dwa parametry.

|Parametr|Opis|
|---------------|-----------------|
|*Nadawcy*|<xref:System.Object> Reprezentujący formant, który spowodował zdarzenie.|
|*e*|A <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> zawierający <xref:Microsoft.Office.Core.IRibbonControl>. Ten formant służy do uzyskania dostępu dowolną właściwość, która nie jest dostępna w modelu obiektów wstążki, które są dostarczane przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|

## <a name="see-also"></a>Zobacz także
- [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Aktualizowanie formantów na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Instrukcje: Dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Instrukcje: Pokaż błędy interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)
