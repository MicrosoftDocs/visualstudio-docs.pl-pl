---
title: XML — Wstążka
description: Dowiedz się, jak używać elementu wstążki (XML), jeśli chcesz dostosować wstążkę w sposób, który nie jest obsługiwany przez element Wstążki (Projektant wizualizacji).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a84a0c21bba42263e7b4dad9ad9118f462389ad6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827503"
---
# <a name="ribbon-xml"></a>XML — Wstążka
  Element wstążki (XML) umożliwia dostosowanie wstążki przy użyciu języka XML. Użyj elementu Wstążki (XML), jeśli chcesz dostosować wstążkę w sposób, który nie jest obsługiwany przez element Wstążki (Projektant wizualny). Aby porównać, co można zrobić z każdym elementem, zobacz [Omówienie wstążki](../vsto/Ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Dodawanie elementu wstążki (XML) do projektu
 Element wstążki **(XML)** można dodać do dowolnego projektu pakietu Office w **oknie dialogowym** Dodawanie nowego elementu. Visual Studio automatycznie dodaje następujące pliki do projektu:

- Plik XML wstążki. Ten plik definiuje interfejs użytkownika wstążki. Ten plik służy do dodawania elementów interfejsu użytkownika, takich jak karty, grupy i kontrolki. Aby uzyskać szczegółowe informacje, zobacz [odwołanie do pliku XML wstążki](#RibbonDescriptorFile) w dalszej części tego tematu.

- Plik kodu wstążki. Ten plik zawiera *klasę wstążki*. Ta klasa ma nazwę określoną dla elementu **wstążki (XML)** w oknie **dialogowym Dodawanie nowego** elementu. Microsoft Office aplikacje używają wystąpienia tej klasy do załadowania niestandardowej wstążki. Aby uzyskać szczegółowe informacje, zobacz [Odwołanie do klas wstążki](#RibbonExtensionClass) w dalszej części tego tematu.

  Domyślnie te pliki dodają grupę niestandardową do karty **Dodatki** na wstążce.

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Wyświetlanie niestandardowej wstążki w Microsoft Office aplikacji
 Po dodaniu elementu wstążki **(XML)** do projektu należy dodać kod do klasy **ThisAddin,** **ThisWorkbook** lub **ThisDocument,** która zastępuje metodę i zwraca klasę XML wstążki do aplikacji `CreateRibbonExtensibilityObject` pakietu Office.

 Poniższy przykład kodu zastępuje metodę i zwraca klasę XML wstążki `CreateRibbonExtensibilityObject` o nazwie MyRibbon.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Definiowanie zachowania niestandardowej wstążki
 Na akcje użytkownika, takie jak kliknięcie przycisku na wstążce, można reagować, tworząc *metody wywołania zwrotnego*. Metody wywołania zwrotnego przypominają zdarzenia Windows Forms kontrolkach, ale są identyfikowane przez atrybut w pliku XML elementu interfejsu użytkownika. Metody są pisane w klasie Wstążki, a kontrolka wywołuje metodę o takiej samej nazwie jak wartość atrybutu. Można na przykład utworzyć metodę wywołania zwrotnego, która jest wywoływana, gdy użytkownik kliknie przycisk na wstążce. Do utworzenia metody wywołania zwrotnego są wymagane dwa kroki:

- Przypisz atrybut do kontrolki w pliku XML wstążki, która identyfikuje metodę wywołania zwrotnego w kodzie.

- Zdefiniuj metodę wywołania zwrotnego w klasie Wstążki.

> [!NOTE]
> Program Outlook wymaga dodatkowego kroku. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wstążki dla programu Outlook.](../vsto/customizing-a-ribbon-for-outlook.md)

 Aby uzyskać przewodnik, który pokazuje, jak zautomatyzować aplikację ze wstążki, zobacz Przewodnik: tworzenie karty niestandardowej [przy użyciu xml wstążki.](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)

### <a name="assign-callback-methods-to-controls"></a>Przypisywanie metod wywołania zwrotnego do kontrolek
 Aby przypisać metodę wywołania zwrotnego do kontrolki w pliku XML wstążki, dodaj atrybut określający typ metody wywołania zwrotnego i nazwę metody . Na przykład poniższy element definiuje przycisk przełączania, który ma metodę wywołania zwrotnego **onAction** o nazwie `OnToggleButton1` .

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 **OnAction** jest wywoływana, gdy użytkownik wykonuje główne zadanie skojarzone z określonej kontrolki. Na przykład metoda wywołania zwrotnego **onAction** przycisku przełączania jest wywoływana, gdy użytkownik kliknie przycisk.

 Metoda określana w atrybutie może mieć dowolną nazwę. Jednak musi odpowiadać nazwie metody, która została zdefiniowana w pliku kodu wstążki.

 Istnieje wiele różnych typów metod wywołania zwrotnego, które można przypisać do kontrolek wstążki. Aby uzyskać pełną listę metod wywołania zwrotnego dostępnych dla każdej kontrolki, zobacz artykuł techniczny [Customize the Office (2007) Ribbon user interface for developers (Part 3 of 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12))(Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 3 z 3) .

### <a name="define-callback-methods"></a><a name="CallBackMethods"></a> Definiowanie metod wywołania zwrotnego
 Zdefiniuj metody wywołania zwrotnego w klasie wstążki w pliku kodu wstążki. Metoda wywołania zwrotnego ma kilka wymagań:

- Musi być zadeklarowana jako publiczna.

- Jego nazwa musi być taka sama jak nazwa metody wywołania zwrotnego, która została przypisana do kontrolki w pliku XML wstążki.

- Jego podpis musi odpowiadać podpisowi typu metody wywołania zwrotnego, który jest dostępny dla skojarzonej kontrolki wstążki.

  Aby uzyskać pełną listę sygnatur metody wywołania zwrotnego dla kontrolek wstążki, zobacz artykuł techniczny [Customize the Office (2007) Ribbon user interface for developers (Part 3 of 3) (Dostosowywanie](/previous-versions/office/developer/office-2007/aa722523(v=office.12))interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 3 z 3) . Visual Studio nie zapewnia obsługi funkcji IntelliSense dla metod wywołania zwrotnego tworzyć w pliku kodu wstążki. Jeśli utworzysz metodę wywołania zwrotnego, która nie pasuje do prawidłowego podpisu, kod zostanie skompilowany, ale nic się nie stanie, gdy użytkownik kliknie kontrolkę.

  Wszystkie metody wywołania zwrotnego mają <xref:Microsoft.Office.Core.IRibbonControl> parametr, który reprezentuje kontrolkę, która wywołała metodę . Tego parametru można użyć do ponownego użycia tej samej metody wywołania zwrotnego dla wielu kontrolek. Poniższy przykład kodu przedstawia metodę wywołania zwrotnego **onAction,** która wykonuje różne zadania w zależności od tego, która kontrolka jest klikana przez użytkownika.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs" id="Snippet2":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb" id="Snippet2":::

## <a name="ribbon-xml-file-reference"></a><a name="RibbonDescriptorFile"></a> Odwołanie do pliku XML wstążki
 Niestandardową wstążkę można zdefiniować, dodając elementy i atrybuty do pliku XML wstążki. Domyślnie plik XML wstążki zawiera następujący kod XML.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">
  <ribbon>
    <tabs>
      <tab idMso="TabAddIns">
        <group id="MyGroup"
               label="My Group">
        </group>
      </tab>
    </tabs>
  </ribbon>
</customUI>
```

 W poniższej tabeli opisano domyślne elementy w pliku XML wstążki.

|Element|Opis|
|-------------|-----------------|
|**customUI**|Reprezentuje niestandardową wstążkę w projekcie dodatku VSTO.|
|**Wstążki**|Reprezentuje wstążkę.|
|**Karty**|Reprezentuje zestaw kart wstążki.|
|**Zakładka**|Reprezentuje pojedynczą kartę wstążki.|
|**Grupa**|Reprezentuje grupę kontrolek na karcie Wstążki.|

 Te elementy mają atrybuty, które określają wygląd i zachowanie niestandardowej wstążki. W poniższej tabeli opisano atrybuty domyślne w pliku XML wstążki.

|Atrybut|Element nadrzędny|Opis|
|---------------|--------------------|-----------------|
|**Onload**|**customUI**|Identyfikuje metodę wywoływaną podczas ładowania wstążki przez aplikację.|
|**idMso**|**Zakładka**|Identyfikuje wbudowaną kartę do wyświetlenia na wstążce.|
|**id**|**Grupa**|Identyfikuje grupę.|
|**Etykiety**|**Grupa**|Określa tekst wyświetlany w grupie.|

 Domyślne elementy i atrybuty w pliku XML wstążki są małym podzbiorem elementów i atrybutów, które są dostępne. Aby uzyskać pełną listę dostępnych elementów i atrybutów, zobacz artykuł techniczny [Customize the Office (2007) Ribbon user interface for developers (Part 2 of 3) (Dostosowywanie](/previous-versions/office/developer/office-2007/aa338199(v=office.12))interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 2 z 3).

## <a name="ribbon-class-reference"></a><a name="RibbonExtensionClass"></a> Odwołanie do klasy wstążki
 Visual Studio generuje klasę wstążki w pliku kodu wstążki. Dodaj metody wywołania zwrotnego dla kontrolek na wstążce do tej klasy. Ta klasa implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility> interfejs .

 W poniższej tabeli opisano metody domyślne w tej klasie.

|Metoda|Opis|
|------------|-----------------|
|`GetCustomUI`|Zwraca zawartość pliku XML wstążki. Microsoft Office wywołują tę metodę w celu uzyskania ciągu XML definiującego interfejs użytkownika niestandardowej wstążki. Ta metoda implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodę . **Uwaga:** `GetCustomUI` należy zaimplementować tylko w celu zwrócenia zawartości pliku XML wstążki; Nie należy go używać do inicjowania dodatku VSTO.   W szczególności nie należy próbować wyświetlać okien dialogowych ani innych okien w `GetCustomUI` implementacji. W przeciwnym razie niestandardowa wstążka może nie zachowywać się poprawnie. Jeśli musisz uruchomić kod, który inicjuje dodatek VSTO, dodaj kod do procedury `ThisAddIn_Startup` obsługi zdarzeń.|
|`OnLoad`|Przypisuje parametr <xref:Microsoft.Office.Core.IRibbonControl> do `Ribbon` pola . Microsoft Office wywołują tę metodę podczas ładowania niestandardowej wstążki. To pole umożliwia dynamiczne aktualizowanie niestandardowej wstążki. Aby uzyskać więcej informacji, zobacz artykuł techniczny Dostosowywanie interfejsu użytkownika wstążki pakietu [Office (2007) dla deweloperów (część 1 z 3).](/previous-versions/office/developer/office-2007/aa338202(v=office.12))|
|`GetResourceText`|Wywoływana `GetCustomUI` przez metodę w celu uzyskania zawartości pliku XML wstążki.|

## <a name="see-also"></a>Zobacz też
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Przewodnik: tworzenie karty niestandardowej przy użyciu xml wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
