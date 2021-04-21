---
title: Omówienie modelu obiektów wstążki
description: Dowiedz się, Visual Studio Tools środowisko uruchomieniowe pakietu Office uwidacznia silnie typowany model obiektów, który umożliwia uzyskiwanie i ustawianie właściwości kontrolek wstążki w czasie wykonywania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f053e87f8cdfd2bdf87bbdf4b7d115f6d9bbec26
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823993"
---
# <a name="ribbon-object-model-overview"></a>Omówienie modelu obiektów wstążki
  Obiekt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] uwidacznia silnie typowany model obiektów, który umożliwia uzyskiwanie i ustawianie właściwości kontrolek wstążki w czasie uruchamiania. Można na przykład dynamicznie wypełniać kontrolki menu lub pokazywać i ukrywać kontrolki kontekstowo. Do wstążki można również dodawać karty, grupy i kontrolki, ale tylko przed załadowaniem wstążki przez aplikację pakietu Office. Aby uzyskać więcej informacji, [zobacz Ustawianie właściwości, które stają się właściwościami tylko do odczytu.](#SettingReadOnlyProperties)

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Ten model obiektów wstążki składa się głównie z klas [Wstążki,](#RibbonClass)zdarzeń [wstążki](#RibbonEvents)i klas [kontrolek wstążki](#RibbonControlClasses).

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Ribbon, klasa
 Po dodaniu nowego elementu **Wstążki (Projektant wizualizacji)** do  projektu Visual Studio klasę wstążki do projektu. Klasa **Wstążki** dziedziczy z <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> klasy .

 Ta klasa jest wyświetlana jako klasa częściowa, która jest dzielona między plik kodu wstążki i plik kodu Projektanta wstążki.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Zdarzenia wstążki
 Klasa **Ribbon** zawiera trzy następujące zdarzenia:

|Zdarzenie|Opis|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Wywoływane, gdy aplikacja pakietu Office ładuje dostosowanie wstążki. Procedura <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> obsługi zdarzeń jest automatycznie dodawana do pliku kodu wstążki. Użyj tej procedury obsługi zdarzeń, aby uruchomić kod niestandardowy podczas ładowania wstążki.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Umożliwia buforowanie obrazów w dostosowywaniu wstążki podczas ładowania wstążki. Możesz uzyskać nieznaczny wzrost wydajności, jeśli napiszesz kod do buforowania obrazów wstążki w tym programie obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Wywoływane po zamknięciu wystąpienia wstążki.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Kontrolki wstążki
 Przestrzeń nazw zawiera typ dla każdej kontrolki, która jest widzina w grupie <xref:Microsoft.Office.Tools.Ribbon> **Kontrolki** wstążki pakietu Office w **przyborniku**.

 W poniższej tabeli przedstawiono typ każdej `Ribbon` kontrolki. Aby uzyskać opis każdej kontrolki, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

|Nazwa kontrolki|Nazwa klasy|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Przycisk**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Rozwijanego**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Galeria**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Grupa**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Etykieta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**Splitbutton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 Przestrzeń nazw używa prefiksu "Ribbon" dla tych typów, aby uniknąć kolizji nazw z nazwami klas <xref:Microsoft.Office.Tools.Ribbon> kontrolek w przestrzeni <xref:System.Windows.Forms> nazw.

 Po dodaniu kontrolki do Projektanta wstążki Projektant wstążki deklaruje klasę dla tej kontrolki jako pole w pliku kodu Projektanta wstążki.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Typowe zadania korzystające z właściwości kontrolek wstążki
 Każda kontrolka zawiera właściwości, których można użyć do wykonywania różnych zadań, takich jak przypisywanie etykiety do kontrolki lub ukrywanie `Ribbon` i pokazywanie kontrolek.

 W niektórych przypadkach właściwości stają się tylko do odczytu po ładowaniu wstążki lub po dodaniu kontrolki do menu dynamicznego. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości, które stają się właściwościami tylko do odczytu.](#SettingReadOnlyProperties)

 W poniższej tabeli opisano niektóre zadania, które można wykonać przy użyciu `Ribbon` właściwości kontrolki.

|Dla tego zadania:|W tym celu:|
|--------------------|--------------|
|Ukrywanie lub pokazywanie kontrolki.|Użyj właściwości Visible.|
|Włącza lub wyłącza kontrolkę.|Użyj właściwości Enabled.|
|Ustaw rozmiar kontrolki.|Użyj właściwości ControlSize.|
|Pobierz obraz wyświetlany na kontrolce.|Użyj właściwości Image.|
|Zmień etykietę kontrolki.|Użyj właściwości Etykieta.|
|Dodawanie danych zdefiniowanych przez użytkownika do kontrolki.|Użyj właściwości Tag.|
|Pobierz elementy w <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> elementach , <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> , <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> lub<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> Kontroli.|Użyj właściwości Items.|
|Dodawanie elementów do <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> kontrolki , <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> lub .|Użyj właściwości Items.|
|Dodaj kontrolki do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> kontrolki .|Użyj właściwości Items.<br /><br /> Aby dodać kontrolki do kontrolki po załadowaniu wstążki do aplikacji pakietu Office, należy ustawić właściwość na true przed załadowaniem wstążki <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> do aplikacji pakietu Office.  Aby uzyskać więcej informacji, [zobacz Ustawianie właściwości, które stają się właściwościami tylko do odczytu.](#SettingReadOnlyProperties)|
|Pobierz wybrany element elementu <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> ,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, lub <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Użyj właściwości SelectedItem. W przypadku <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> obiektu użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> właściwości .|
|Pobierz grupy do grupy <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> .|Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> właściwości .|
|Określ liczbę wierszy i kolumn wyświetlanych w tabeli <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Użyj właściwości <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> i .|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Ustawianie właściwości, które stają się tylko do odczytu
 Niektóre właściwości można ustawić tylko przed ładowaniem wstążki. Te właściwości można ustawić w trzech miejscach:

- W oknie Visual Studio **właściwości.**

- W konstruktorze klasy **Wstążki.**

- W `CreateRibbonExtensibilityObject` metodzie klasy `ThisAddin` `ThisWorkbook` , lub `ThisDocument` projektu.

  Menu dynamiczne zapewniają pewne wyjątki. Możesz tworzyć nowe kontrolki, ustawiać ich właściwości, a następnie dodawać je do menu dynamicznego w czasie uruchamiania, nawet po załadowaniu wstążki zawierającej menu.

  Właściwości kontrolek, które dodajesz do menu dynamicznego, można ustawić w dowolnym momencie.

  Aby uzyskać więcej informacji, zobacz [Właściwości, które stają się właściwościami tylko do odczytu.](#ReadOnlyProperties)

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Ustawianie właściwości w konstruktorze wstążki
 Właściwości kontrolki można ustawić `Ribbon` w konstruktorze klasy **Wstążki.** Ten kod musi pojawić się po wywołaniu `InitializeComponent` metody . Poniższy przykład dodaje nowy przycisk do grupy, jeśli bieżąca godzina to 17:00 czasu pacyficznego (UTC-8) lub nowsza.

 Dodaj następujący kod.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb" id="Snippet1":::

 W projektach Visual C# uaktualnionych z wersji Visual Studio 2008 konstruktor pojawia się w pliku kodu wstążki.

 W Visual Basic projektach lub projektach Visual C# utworzonych w programie konstruktor pojawia się w pliku kodu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] Projektanta wstążki. Ten plik nosi nazwę *YourRibbonItem.* Designer.cs lub *YourRibbonItem.* Designer.vb. Aby wyświetlić ten plik w Visual Basic projektach, należy najpierw kliknąć przycisk Pokaż wszystkie **pliki** w Eksplorator rozwiązań.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Ustawianie właściwości w metodzie CreateRibbonExtensibilityObject
 Właściwości kontrolki można ustawić podczas zastępowania metody w `Ribbon` `CreateRibbonExtensibilityObject` klasie , lub `ThisAddin` `ThisWorkbook` `ThisDocument` projektu. Aby uzyskać więcej informacji na temat `CreateRibbonExtensibilityObject` metody , zobacz [Wstążka — omówienie](../vsto/ribbon-overview.md).

 Poniższy przykład ustawia właściwości wstążki w `CreateRibbonExtensibilityObject` metodzie `ThisWorkbook` klasy projektu skoroszytu programu Excel.

 Dodaj następujący kod.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs" id="Snippet2":::

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Właściwości, które stają się właściwościami tylko do odczytu
 W poniższej tabeli przedstawiono właściwości, które można ustawić tylko przed ładowaniem wstążki.

> [!NOTE]
> Właściwości kontrolek w menu dynamicznym można ustawić w dowolnym momencie. W takim przypadku ta tabela nie ma zastosowania.

|Właściwość|Klasa kontrolki wstążki|
|--------------|--------------------------|
|**Styl boxstyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Buttontype**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Columncount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Controlid**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**Okno dialogoweUncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dynamiczny**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Globalnie**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Grupy**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**Imagename**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**Itemsize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Maxlength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Nazwa**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Pozycja**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**Typ wstążki**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Rowcount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Karty**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Tytuł**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Ustawianie właściwości wstążek wyświetlanych w inspektorach programu Outlook
 Nowe wystąpienie wstążki jest tworzone za każdym razem, gdy użytkownik otwiera inspektora, w którym jest wyświetlana wstążka. Właściwości wymienione w powyższej tabeli można jednak ustawić tylko przed utworzeniem pierwszego wystąpienia wstążki. Po utworzeniu pierwszego wystąpienia te właściwości stają się właściwościami tylko do odczytu, ponieważ pierwsze wystąpienie definiuje plik XML używany przez program Outlook do załadowania wstążki.

 Jeśli masz logikę warunkową, która ustawia dowolną z tych właściwości na inną wartość podczas tworzenia innych wystąpień wstążki, ten kod nie będzie mieć żadnego efektu.

> [!NOTE]
> Upewnij się, **że właściwość Name** jest ustawiona dla każdej kontrolki, która jest dodawania do wstążki programu Outlook. Jeśli dodasz kontrolkę do wstążki programu Outlook w czasie uruchamiania, musisz ustawić tę właściwość w kodzie. Jeśli dodasz kontrolkę do wstążki programu Outlook w czasie projektowania, właściwość Name zostanie ustawiona automatycznie.

## <a name="ribbon-control-events"></a>Zdarzenia kontrolki wstążki
 Każda klasa kontrolek zawiera jedno lub więcej zdarzeń. W poniższej tabeli opisano te zdarzenia.

|Zdarzenie|Opis|
|-----------|-----------------|
|Kliknij|Występuje po kliknięciu kontrolki.|
|Textchanged|Występuje po zmianie tekstu pola edycji lub pola kombi.|
|ElementyŁadowanie|Występuje, gdy pakiet Office żąda kolekcji Items kontrolki. Pakiet Office buforuje kolekcję Items do momentu zmiany właściwości kontrolki przez kod lub wywołania <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> metody .|
|PrzyciskKliknij|Występuje po kliknięciu <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> przycisku <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> w lub .|
|Selectionchanged|Występuje, gdy wybór w <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> lub <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> zmienia.|
|DialogLauncherClick|Występuje po kliknięciu ikony uruchamiania okna dialogowego w prawym dolnym rogu grupy.|

 Procedury obsługi zdarzeń dla tych zdarzeń mają następujące dwa parametry.

|Parametr|Opis|
|---------------|-----------------|
|*Nadawcy*|Element <xref:System.Object> reprezentujący kontrolkę, która wywłaszowała zdarzenie.|
|*E*|, <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> który zawiera . <xref:Microsoft.Office.Core.IRibbonControl> Użyj tej kontrolki, aby uzyskać dostęp do dowolnej właściwości, która nie jest dostępna w modelu obiektów wstążki dostarczonym przez obiekt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|

## <a name="see-also"></a>Zobacz też
- [Uzyskiwanie dostępu do wstążki w czasie uruchamiania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [How to: Get started customizing the ribbon (Jak rozpocząć dostosowywanie wstążki)](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Przewodnik: tworzenie karty niestandardowej przy użyciu Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: aktualizowanie kontrolek na wstążce w czasie uruchamiania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Jak dostosować wbudowaną kartę](../vsto/how-to-customize-a-built-in-tab.md)
- [Jak dodać kontrolki do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [How to: Export a ribbon from the Ribbon Designer to Ribbon XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Instrukcji: pokazywanie błędów interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)
