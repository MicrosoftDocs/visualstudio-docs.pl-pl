---
title: Omówienie modelu obiektów wstążki
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
ms.openlocfilehash: 6ca22704345fefb4944bda7dd9f71942fe8dfb50
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256015"
---
# <a name="ribbon-object-model-overview"></a>Omówienie modelu obiektów wstążki
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Uwidacznia model obiektów o jednoznacznie określonym typie, którego można użyć do pobierania i ustawiania właściwości kontrolek wstążki w czasie wykonywania. Na przykład można dynamicznie wypełniać kontrolki menu lub wyświetlać i ukrywać kontrolki w sposób kontekstowy. Możesz również dodawać karty, grupy i kontrolki do wstążki, ale tylko przed załadowaniem Wstążki przez aplikację pakietu Office. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości, które stają się tylko do odczytu](#SettingReadOnlyProperties).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Ten model obiektów wstążki składa się głównie z [klasy wstążki](#RibbonClass), [zdarzeń wstążki](#RibbonEvents)i [klas kontrolek wstążki](#RibbonControlClasses).

## <a name="RibbonClass"></a>Klasa wstążki
 Po dodaniu nowego elementu **wstążki (projektant graficzny)** do projektu, Visual Studio dodaje klasę **wstążki** do projektu. Klasa **wstążki** dziedziczy z <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> klasy.

 Ta klasa jest wyświetlana jako Klasa częściowa, która jest podzielona między plik kodu wstążki i plik kodu projektanta wstążki.

## <a name="RibbonEvents"></a>Zdarzenia wstążki
 Klasa **wstążki** zawiera trzy następujące zdarzenia:

|Zdarzenie|Opis|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Uruchamiany, gdy aplikacja pakietu Office załaduje dostosowanie wstążki. Procedura <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> obsługi zdarzeń jest automatycznie dodawana do pliku kodu wstążki. Użyj tego programu obsługi zdarzeń, aby uruchomić kod niestandardowy podczas ładowania wstążki.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Umożliwia buforowanie obrazów na potrzeby dostosowywania wstążki podczas ładowania wstążki. Możesz uzyskać niewielki wzrost wydajności, jeśli piszesz kod w celu buforowania obrazów wstążki w tym obsłudze zdarzeń. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Uruchamiany, gdy wystąpienie wstążki zostanie zamknięte.|

## <a name="RibbonControlClasses"></a>Kontrolki wstążki
 Przestrzeń nazw zawiera typ dla każdej kontrolki widocznej w grupie **kontrolki wstążki pakietu Office** w **przyborniku.** <xref:Microsoft.Office.Tools.Ribbon>

 W poniższej tabeli przedstawiono typ dla każdej `Ribbon` kontrolki. Aby zapoznać się z opisem poszczególnych kontrolek, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

|Nazwa kontrolki|Nazwa klasy|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Przycisk**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Przyjmij**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Galeria**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Grupa**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Etykieta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Karta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 Przestrzeń nazw używa prefiksu "wstążka" dla tych typów, aby uniknąć kolizji nazw z nazwami klas kontroli <xref:System.Windows.Forms> w przestrzeni nazw. <xref:Microsoft.Office.Tools.Ribbon>

 Po dodaniu kontrolki do projektanta wstążki Projektant wstążki deklaruje klasę dla tej kontrolki jako pole w pliku kodu projektanta wstążki.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Typowe zadania przy użyciu właściwości kontrolek wstążki
 Każda `Ribbon` kontrolka zawiera właściwości, których można użyć do wykonywania różnych zadań, takich jak przypisywanie etykiety do kontrolki lub ukrywanie i pokazywanie kontrolek.

 W niektórych przypadkach właściwości stają się tylko do odczytu po załadowaniu wstążki lub po dodaniu kontrolki do menu dynamicznego. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości, które stają się tylko do odczytu](#SettingReadOnlyProperties).

 W poniższej tabeli opisano niektóre zadania, które można wykonać przy użyciu `Ribbon` właściwości kontrolki.

|Dla tego zadania:|Wykonaj następujące czynności:|
|--------------------|--------------|
|Ukryj lub Pokaż kontrolkę.|Użyj właściwości Visible.|
|Włączać lub wyłączać kontrolkę.|Użyj właściwości Enabled.|
|Ustaw rozmiar kontrolki.|Użyj właściwości ControlSize.|
|Pobierz obraz, który pojawia się na kontrolce.|Użyj właściwości Image.|
|Zmień etykietę kontrolki.|Użyj właściwości etykieta.|
|Dodaj dane zdefiniowane przez użytkownika do kontrolki.|Użyj właściwości tag.|
|Pobierz elementy w <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>lub<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>kontroli.|Użyj właściwości Items.|
|Dodaj elementy do <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>kontrolki <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>,, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> lub.|Użyj właściwości Items.|
|Dodaj formanty do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Użyj właściwości Items.<br /><br /> Aby dodać formanty do programu <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po załadowaniu wstążki do aplikacji pakietu Office, należy <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> ustawić właściwość na **wartość true** przed załadowaniem Wstążki do aplikacji pakietu Office. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości, które stają się tylko do odczytu](#SettingReadOnlyProperties).|
|Pobierz wybrany element <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>lub <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Użyj właściwości SelectedItem. Dla elementu <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> należy użyć właściwości.|
|Pobierz grupy na <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> Użyj właściwości.|
|Określ liczbę wierszy i kolumn, które pojawiają się w <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Użyj właściwości <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>i. <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>|

## <a name="SettingReadOnlyProperties"></a>Ustawianie właściwości, które stają się tylko do odczytu
 Niektóre właściwości można ustawić tylko przed załadowaniem Wstążki. Istnieją trzy miejsca, w których można ustawić następujące właściwości:

- W oknie **Właściwości** programu Visual Studio.

- W konstruktorze klasy **wstążki** .

- W metodzie `ThisAddin` ,`ThisWorkbook`, lub`ThisDocument`klasyprojektu. `CreateRibbonExtensibilityObject`

  Menu dynamiczne zawierają pewne wyjątki. Można utworzyć nowe kontrolki, ustawić ich właściwości, a następnie dodać je do dynamicznego menu w czasie wykonywania, nawet po załadowaniu wstążki zawierającej menu.

  Właściwości kontrolek dodawanych do menu dynamicznego można ustawić w dowolnym momencie.

  Aby uzyskać więcej informacji, zobacz [właściwości, które stają się tylko do odczytu](#ReadOnlyProperties).

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Ustawianie właściwości w konstruktorze wstążki
 Można ustawić właściwości `Ribbon` kontrolki w konstruktorze klasy **wstążki** . Ten kod musi występować po wywołaniu `InitializeComponent` metody. Poniższy przykład dodaje nowy przycisk do grupy, jeśli bieżący czas to 17:00 czasu pacyficznego (UTC-8) lub nowszego.

 Dodaj następujący kod.

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 W projektach C# wizualnych uaktualnionych z programu visual Studio 2008 Konstruktor pojawia się w pliku kodu wstążki.

 W projektach Visual Basic lub w projektach wizualnych C# utworzonych w programie [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]Konstruktor pojawia się w pliku kodu projektanta wstążki. Ten plik ma nazwę *YourRibbonItem*. Designer.cs lub *YourRibbonItem*. Designer. vb. Aby wyświetlić ten plik w projektach Visual Basic, należy najpierw kliknąć przycisk **Pokaż wszystkie pliki** w Eksplorator rozwiązań.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Ustawianie właściwości w metodzie CreateRibbonExtensibilityObject
 Można ustawić `Ribbon` właściwości kontrolki podczas `ThisAddin` `CreateRibbonExtensibilityObject` przesłonięcia metody w, `ThisWorkbook`, lub `ThisDocument` klasy projektu. Aby uzyskać więcej informacji na `CreateRibbonExtensibilityObject` temat metody, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

 Poniższy przykład ustawia właściwości wstążki w `CreateRibbonExtensibilityObject` metodzie `ThisWorkbook` klasy projektu skoroszytu programu Excel.

 Dodaj następujący kod.

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="ReadOnlyProperties"></a>Właściwości, które stają się tylko do odczytu
 W poniższej tabeli przedstawiono właściwości, które można ustawić tylko przed załadowaniem Wstążki.

> [!NOTE]
> W dowolnym momencie można ustawić właściwości kontrolek w menu dynamicznym. Ta tabela nie ma zastosowania w tym przypadku.

|Właściwość|Klasa kontrolki wstążki|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Kolumn**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dynamic**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Grupowania**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Nazwa**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Stanowisko**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**Wstążka**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Liczby wierszy**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Karty**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Tytuł**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Ustawianie właściwości dla wstążki, które pojawiają się w inspektorach programu Outlook
 Nowe wystąpienie wstążki jest tworzone za każdym razem, gdy użytkownik otwiera inspektora, w którym pojawia się wstążka. Można jednak ustawić właściwości wymienione w powyższej tabeli tylko przed utworzeniem pierwszego wystąpienia wstążki. Po utworzeniu pierwszego wystąpienia te właściwości stają się tylko do odczytu, ponieważ pierwsze wystąpienie definiuje plik XML, który jest wykorzystywany przez program Outlook do załadowania wstążki.

 Jeśli istnieje logika warunkowa, która ustawia dowolne z tych właściwości na inną wartość, gdy tworzone są inne wystąpienia wstążki, ten kod nie będzie miał żadnego efektu.

> [!NOTE]
> Upewnij się, że właściwość **name** jest ustawiona dla każdej kontrolki, która została dodana do wstążki programu Outlook. Po dodaniu kontrolki do wstążki programu Outlook w czasie wykonywania należy ustawić tę właściwość w kodzie. Po dodaniu kontrolki do wstążki programu Outlook w czasie projektowania właściwość Name jest ustawiana automatycznie.

## <a name="ribbon-control-events"></a>Zdarzenia kontrolki wstążki
 Każda Klasa kontrolki zawiera jedno lub więcej zdarzeń. W poniższej tabeli opisano te zdarzenia.

|Zdarzenie|Opis|
|-----------|-----------------|
|Kliknij|Występuje, gdy formant zostanie kliknięty.|
|Textchanged.|Występuje, gdy zostanie zmieniony tekst pola edycji lub pola kombi.|
|ItemsLoading|Występuje po zażądaniu przez Urząd kolekcji elementów formantu. Pakiet Office buforuje kolekcję elementów do momentu, gdy kod zmieni właściwości kontrolki lub wywoła <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> metodę.|
|ButtonClick|Występuje, gdy zostanie kliknięty <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> przycisk <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> w lub.|
|SelectionChanged|Występuje, gdy zmieni się zaznaczenie <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> w <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> lub.|
|DialogLauncherClick|Występuje, gdy zostanie kliknięta ikona uruchamiania okna dialogowego w prawym dolnym rogu grupy.|

 Procedury obsługi zdarzeń dla tych zdarzeń mają następujące dwa parametry.

|Parametr|Opis|
|---------------|-----------------|
|*Sender*|<xref:System.Object> Reprezentuje kontrolkę, która wywołała zdarzenie.|
|*e*|A <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> , który <xref:Microsoft.Office.Core.IRibbonControl>zawiera. Użyj tego formantu, aby uzyskać dostęp do dowolnej właściwości, która nie jest dostępna w modelu obiektu wstążki [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]dostarczonego przez.|

## <a name="see-also"></a>Zobacz także
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Aktualizowanie kontrolek na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Instrukcje: Dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Instrukcje: Eksportowanie wstążki z projektanta wstążki do kodu XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Instrukcje: Pokaż błędy interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)
