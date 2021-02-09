---
title: XML — Wstążka
description: Dowiedz się, jak używać elementu wstążki (XML), jeśli chcesz dostosować Wstążkę w sposób, który nie jest obsługiwany przez Wstążkę (Projektant wizualizacji).
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
ms.openlocfilehash: 69ca0269859db9e1a69904c2211b8f4d1ad45710
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879296"
---
# <a name="ribbon-xml"></a>XML — Wstążka
  Element wstążki (XML) umożliwia dostosowanie wstążki przy użyciu kodu XML. Użyj elementu wstążki (XML), jeśli chcesz dostosować Wstążkę w sposób, który nie jest obsługiwany przez Wstążkę (projektant graficzny). Aby zapoznać się z porównaniem możliwości poszczególnych elementów, zobacz [Omówienie wstążki](../vsto/Ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Dodaj element wstążki (XML) do projektu
 Możesz dodać element **wstążki (XML)** do dowolnego projektu pakietu Office z okna dialogowego **Dodaj nowy element** . Program Visual Studio automatycznie dodaje do projektu następujące pliki:

- Plik XML wstążki. Ten plik definiuje interfejs użytkownika wstążki (UI). Użyj tego pliku, aby dodać elementy interfejsu użytkownika, takie jak karty, grupy i formanty. Aby uzyskać szczegółowe informacje, zobacz [Informacje o pliku XML wstążki](#RibbonDescriptorFile) w dalszej części tego tematu.

- Plik kodu wstążki. Ten plik zawiera *klasę wstążki*. Ta klasa ma nazwę określoną dla elementu **wstążki (XML)** w oknie dialogowym **Dodaj nowy element** . Aplikacje Microsoft Office używają wystąpienia tej klasy do załadowania Wstążki niestandardowej. Aby uzyskać szczegółowe informacje, zobacz [Informacje o klasie wstążki](#RibbonExtensionClass) w dalszej części tego tematu.

  Domyślnie te pliki dodają grupę niestandardową do karty **Dodatki** na Wstążce.

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Wyświetlanie Wstążki niestandardowej w aplikacji Microsoft Office
 Po dodaniu elementu **wstążki (XML)** do projektu, musisz dodać kod do klasy **ThisAddIn**, **ThisWorkbook** lub **ThisDocument** , która zastępuje `CreateRibbonExtensibilityObject` metodę i zwraca klasę XML wstążki do aplikacji pakietu Office.

 Poniższy przykład kodu przesłania `CreateRibbonExtensibilityObject` metodę i zwraca klasę XML wstążki o nazwie Moja wstążka.

 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Definiowanie zachowania Wstążki niestandardowej
 Możesz odpowiedzieć na akcje użytkownika, na przykład klikając przycisk na Wstążce, tworząc *metody wywołania zwrotnego*. Metody wywołania zwrotnego przypominają zdarzenia w kontrolkach Windows Forms, ale są identyfikowane przez atrybut w XML elementu interfejsu użytkownika. Metody pisania w klasie wstążki, a kontrolka wywołuje metodę, która ma taką samą nazwę jak wartość atrybutu. Na przykład można utworzyć metodę wywołania zwrotnego, która jest wywoływana, gdy użytkownik kliknie przycisk na Wstążce. Do utworzenia metody wywołania zwrotnego wymagane są dwa kroki:

- Przypisz atrybut do kontrolki w pliku XML wstążki, który identyfikuje metodę wywołania zwrotnego w kodzie.

- Zdefiniuj metodę wywołania zwrotnego w klasie wstążki.

> [!NOTE]
> Program Outlook wymaga dodatkowego kroku. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

 Aby zapoznać się z przewodnikiem, który pokazuje, jak zautomatyzować aplikację ze wstążki, zobacz [Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).

### <a name="assign-callback-methods-to-controls"></a>Przypisywanie metod wywołania zwrotnego do kontrolek
 Aby przypisać metodę wywołania zwrotnego do kontrolki w pliku XML wstążki, Dodaj atrybut, który określa typ metody wywołania zwrotnego i nazwę metody. Na przykład poniższy element definiuje przycisk przełączania, który ma metodę wywołania zwrotnego **OnAction** o nazwie `OnToggleButton1` .

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 **Akcja OnAction** jest wywoływana, gdy użytkownik wykonuje główne zadanie skojarzone z konkretną kontrolką. Na przykład metoda wywołania zwrotnego **OnAction** przycisku przełącznika jest wywoływana, gdy użytkownik kliknie przycisk.

 Metoda określona w atrybucie może mieć dowolną nazwę. Jednak musi być zgodna z nazwą metody, która została zdefiniowana w pliku kodu wstążki.

 Istnieje wiele różnych typów metod wywołania zwrotnego, które można przypisać do kontrolek wstążki. Aby zapoznać się z pełną listą metod wywołania zwrotnego dostępnych dla poszczególnych kontrolek, zobacz artykuł techniczny [: Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 3 z 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)).

### <a name="define-callback-methods"></a><a name="CallBackMethods"></a> Definiuj metody wywołania zwrotnego
 Zdefiniuj metody wywołania zwrotnego w klasie wstążki w pliku kodu wstążki. Metoda wywołania zwrotnego ma kilka wymagań:

- Musi być zadeklarowana jako publiczna.

- Jego nazwa musi być zgodna z nazwą metody wywołania zwrotnego, która została przypisana do kontrolki w pliku XML wstążki.

- Jego sygnatura musi być zgodna z sygnaturą typu metody wywołania zwrotnego, która jest dostępna dla skojarzonej kontrolki wstążki.

  Aby uzyskać pełną listę sygnatur metody wywołania zwrotnego dla kontrolek wstążki, zobacz artykuł techniczny [: Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 3 z 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)). Program Visual Studio nie zapewnia obsługi technologii wywołania zwrotnego w pliku kodu wstążki. Jeśli utworzysz metodę wywołania zwrotnego, która nie jest zgodna z prawidłowym podpisem, kod zostanie skompilowany, ale nic się nie pojawi, gdy użytkownik kliknie formant.

  Wszystkie metody wywołania zwrotnego mają <xref:Microsoft.Office.Core.IRibbonControl> parametr, który reprezentuje kontrolkę, która wywołała metodę. Tego parametru można użyć do wielokrotnego użycia tej samej metody wywołania zwrotnego dla wielu kontrolek. Poniższy przykład kodu demonstruje metodę wywołania zwrotnego **OnAction** , która wykonuje różne zadania w zależności od tego, która kontrolka klika użytkownika.

  [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
  [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]

## <a name="ribbon-xml-file-reference"></a><a name="RibbonDescriptorFile"></a> Dokumentacja pliku XML wstążki
 Możesz zdefiniować własną Wstążkę, dodając elementy i atrybuty do pliku XML wstążki. Domyślnie plik XML wstążki zawiera następujący kod XML.

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

 W poniższej tabeli opisano elementy domyślne w pliku XML wstążki.

|Element|Opis|
|-------------|-----------------|
|**customUI**|Reprezentuje Wstążkę niestandardową w projekcie dodatku VSTO.|
|**wstążki**|Reprezentuje Wstążkę.|
|**przedstawia**|Reprezentuje zestaw kart wstążki.|
|**tabulator**|Przedstawia pojedynczą kartę wstążki.|
|**Group**|Reprezentuje grupę kontrolek na karcie wstążki.|

 Te elementy mają atrybuty, które określają wygląd i zachowanie Wstążki niestandardowej. W poniższej tabeli opisano atrybuty domyślne w pliku XML wstążki.

|Atrybut|Element nadrzędny|Opis|
|---------------|--------------------|-----------------|
|**onLoad**|**customUI**|Identyfikuje metodę, która jest wywoływana, gdy aplikacja ładuje Wstążkę.|
|**idMso**|**tabulator**|Identyfikuje wbudowaną kartę, która ma zostać wyświetlona na Wstążce.|
|**id**|**Group**|Identyfikuje grupę.|
|**oznakowan**|**Group**|Określa tekst, który pojawia się w grupie.|

 Domyślne elementy i atrybuty w pliku XML wstążki są małym podzbiorem dostępnych elementów i atrybutów. Aby uzyskać pełną listę dostępnych elementów i atrybutów, zapoznaj się z artykułem technicznym [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 2 z 3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12)).

## <a name="ribbon-class-reference"></a><a name="RibbonExtensionClass"></a> Odwołanie do klasy wstążki
 Program Visual Studio generuje klasę wstążki w pliku kodu wstążki. Dodaj metody wywołania zwrotnego dla formantów na Wstążce do tej klasy. Ta klasa implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility> interfejs.

 W poniższej tabeli opisano metody domyślne w tej klasie.

|Metoda|Opis|
|------------|-----------------|
|`GetCustomUI`|Zwraca zawartość pliku XML wstążki. Microsoft Office aplikacje wywołują tę metodę, aby uzyskać ciąg XML definiujący interfejs użytkownika wstążki niestandardowej. Ta metoda implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodę. **Uwaga:** `GetCustomUI` należy zaimplementować tylko w celu zwrócenia zawartości pliku XML wstążki; nie należy używać go do inicjowania dodatku VSTO.   W szczególności nie należy próbować wyświetlać okien dialogowych ani innych okien w `GetCustomUI` implementacji. W przeciwnym razie wstążka niestandardowa może nie działać poprawnie. Jeśli musisz uruchomić kod inicjujący dodatek VSTO, Dodaj kod do `ThisAddIn_Startup` programu obsługi zdarzeń.|
|`OnLoad`|Przypisuje <xref:Microsoft.Office.Core.IRibbonControl> parametr do `Ribbon` pola. Microsoft Office aplikacje wywołują tę metodę, gdy ładują Wstążkę niestandardową. To pole służy do dynamicznego aktualizowania Wstążki niestandardowej. Aby uzyskać więcej informacji, zapoznaj się z artykułem technicznym [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 1 z 3)](/previous-versions/office/developer/office-2007/aa338202(v=office.12)).|
|`GetResourceText`|Wywoływane przez `GetCustomUI` metodę, aby uzyskać zawartość pliku XML wstążki.|

## <a name="see-also"></a>Zobacz też
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
