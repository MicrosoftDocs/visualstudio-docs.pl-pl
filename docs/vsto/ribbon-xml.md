---
title: XML — Wstążka
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 77fa9442289851aff91d8d9bfc55e581edfa774a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117547"
---
# <a name="ribbon-xml"></a>XML — Wstążka
  Element wstążki (XML) umożliwia dostosowywanie wstążki przy użyciu języka XML. Jeśli chcesz dostosowania wstążki w taki sposób, że nie jest obsługiwany przez element wstążki (Projektant graficzny), należy użyć elementu wstążki (XML). Porównanie co można zrobić z każdym elementem, zobacz [Wstążka ― omówienie](../vsto/Ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Dodaj element wstążki (XML) do projektu
 Możesz dodać **wstążki (XML)** element do jakiegokolwiek projektu pakietu Office z **Dodaj nowy element** okno dialogowe. Visual Studio automatycznie dodaje następujące pliki do projektu:

- Plik XML wstążki. Ten plik definiuje interfejs użytkownika wstążki (UI). Użyj tego pliku, aby dodać elementy interfejsu użytkownika, takie jak karty, grupy i formanty. Aby uzyskać więcej informacji, zobacz [odwołanie do pliku XML wstążki](#RibbonDescriptorFile) w dalszej części tego tematu.

- Plik kodu wstążki. Ten plik zawiera *wstążki klasy*. Ta klasa ma nazwę, który został określony dla **wstążki (XML)** pozycja **Dodaj nowy element** okno dialogowe. Aplikacje Microsoft Office Użyj wystąpienia tej klasy, aby załadować niestandardowa Wstążka. Aby uzyskać więcej informacji, zobacz [wstążki odwołań do klas](#RibbonExtensionClass) w dalszej części tego tematu.

  Domyślnie te pliki, dodawać niestandardową grupę do **Add-Ins** kartę na Wstążce.

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Wyświetlanie niestandardowych wstążki w aplikacji pakietu Microsoft Office
 Po dodaniu **wstążki (XML)** elementu do projektu, należy dodać kod, aby **ThisAddin**, **ThisWorkbook**, lub **ThisDocument** klasy który zastępuje `CreateRibbonExtensibilityObject` metodę i zwraca XML wstążki klasy do aplikacji pakietu Office.

 Poniższy kod przykład zastąpienia `CreateRibbonExtensibilityObject` metodę i zwraca XML wstążki klasy o nazwie MyRibbon.

 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Zdefiniuj zachowanie niestandardowa Wstążka
 Pozwalające reagować na działania użytkownika, takie jak kliknięcie przycisku na Wstążce, tworząc *metody wywołania zwrotnego*. Metody wywołania zwrotnego przypominają zdarzenia w kontrolkach formularzy Windows Forms, ale są one zidentyfikowane przez atrybut w XML elementu interfejsu użytkownika. Pisanie metod w klasie Wstążki i kontrolki wywołuje metodę, która ma taką samą nazwę jak wartość atrybutu. Na przykład można utworzyć metody wywołania zwrotnego, która jest wywoływana, gdy użytkownik kliknie przycisk na Wstążce. Dwa kroki są wymagane do utworzenia metody wywołania zwrotnego:

- Przypisz atrybut do formantu w pliku XML wstążki, który identyfikuje metodę wywołania zwrotnego w kodzie.

- Zdefiniuj metodę wywołania zwrotnego w klasie wstążki.

> [!NOTE]
>  Program Outlook wymaga dodatkowego kroku. Aby uzyskać więcej informacji, zobacz [Dostosuj Wstążkę dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

 Aby wskazówki, który demonstruje sposób automatyzacja aplikacji z poziomu wstążki, zobacz [instruktażu: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).

### <a name="assign-callback-methods-to-controls"></a>Przypisz metody wywołania zwrotnego do formantów
 Aby przypisać metody wywołania zwrotnego do formantu w pliku XML wstążki, Dodaj atrybut, który określa typ metody wywołania zwrotnego i nazwę metody. Na przykład, następujący element definiuje przycisk przełącznika, który ma **onAction** metody wywołania zwrotnego o nazwie `OnToggleButton1`.

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 **onAction** jest wywoływana, gdy użytkownik wykonuje głównym zadaniem, które są skojarzone z określonego formantu. Na przykład **onAction** metody wywołania zwrotnego przycisku przełącznika jest wywoływana, gdy użytkownik kliknie przycisk.

 Metoda, który określisz w atrybucie może mieć dowolną nazwę. Jednakże musi być zgodna Nazwa metody zdefiniowanej w pliku kodu wstążki.

 Istnieje wiele różnych typów, metod wywołania zwrotnego, które można przypisać do formantów wstążki. Pełną listę dostępnych metod wywołania zwrotnego dla każdego formantu, zobacz artykuł techniczny [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 3 z 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)).

### <a name="CallBackMethods"></a> Definiowania metod wywoływania zwrotnego
 Zdefiniuj metody wywołania zwrotnego w klasie wstążki w pliku kodu wstążki. Metoda wywołania zwrotnego ma kilka wymagań:

- Musi być zadeklarowany jako publiczny.

- Jej nazwa musi odpowiadać Nazwa metody wywołania zwrotnego, która została przypisana do formantu w pliku XML wstążki.

- Jeho signatura musi odpowiadać podpisowi typu metody wywołania zwrotnego, który jest dostępny dla skojarzonego formantu wstążki.

  Aby uzyskać pełną listę podpisy metod wywołania zwrotnego dla formantów wstążki, zobacz artykułu technicznego [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 3 z 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)). Program Visual Studio nie zapewnia obsługę technologii IntelliSense dla metody wywołania zwrotnego, które tworzysz w pliku kodu wstążki. Jeśli tworzysz metodę wywołania zwrotnego niezgodny prawidłowego podpisu, poniższy kod zostanie skompilowany, ale nic nie wystąpi, gdy użytkownik kliknie kontrolkę.

  Wszystkie metody wywołania zwrotnego mają <xref:Microsoft.Office.Core.IRibbonControl> parametr, który reprezentuje kontrolkę która jest wywoływana metoda. Ten parametr umożliwia ponowne użycie tej samej metody wywołania zwrotnego w przypadku wielu kontrolek. Poniższy przykład kodu demonstruje **onAction** metody wywołania zwrotnego, który wykonuje różne zadania, w zależności od tego, które klika formant użytkownika.

  [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
  [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]

## <a name="RibbonDescriptorFile"></a> Odwołanie do pliku XML wstążki
 Można zdefiniować swoje niestandardowa Wstążka przez dodanie elementów i atrybutów do pliku XML wstążki. Domyślnie plik XML wstążki zawiera następujący kod XML.

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
|**customUI**|Reprezentuje niestandardowa Wstążka w projekcie dodatku narzędzi VSTO.|
|**Wstążki**|Reprezentuje wstążki.|
|**Karty**|Reprezentuje zestaw kart wstążki.|
|**Karta**|Reprezentuje pojedynczy karty wstążki.|
|**Grupy**|Reprezentuje grupę kontrolek na karcie wstążki.|

 Te elementy mają atrybuty, które określają wygląd i zachowanie niestandardowa Wstążka. W poniższej tabeli opisano atrybuty domyślnych w pliku XML wstążki.

|Atrybut|Element nadrzędny|Opis|
|---------------|--------------------|-----------------|
|**onLoad**|**customUI**|Określa metodę, która jest wywoływana, gdy aplikacja ładuje wstążki.|
|**idMso**|**Karta**|Identyfikuje wbudowanej karty do wyświetlenia na Wstążce.|
|**id**|**Grupy**|Identyfikuje grupę.|
|**Etykieta**|**Grupy**|Określa tekst, który pojawia się w grupie.|

 Domyślne elementy i atrybuty w pliku XML wstążki są mały podzbiór elementów i atrybutów, które są dostępne. Aby uzyskać pełną listę dostępnych elementów i atrybutów, zobacz artykułu technicznego [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 2 z 3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12)).

## <a name="RibbonExtensionClass"></a> Informacje o klasach wstążki
 Program Visual Studio generuje klasę wstążki w pliku kodu wstążki. Dodaj metody wywołania zwrotnego dla formantów na Wstążce do tej klasy. Ta klasa implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility> interfejsu.

 W poniższej tabeli opisano domyślnych metod w tej klasie.

|Metoda|Opis|
|------------|-----------------|
|`GetCustomUI`|Zwraca zawartość pliku XML wstążki. Aplikacje Microsoft Office wywołać tę metodę w celu uzyskania ciągu XML, który definiuje interfejs użytkownika usługi niestandardowa Wstążka. Ta metoda implementuje <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metody. **Uwaga:** `GetCustomUI` powinny zostać wdrożone tylko, aby zwrócić zawartość pliku XML wstążki, np; nie powinno być używane można zainicjować dodatku narzędzi VSTO dla programów. W szczególności, nie powinno się wyświetlanie okien dialogowych lub innych oknach swoje `GetCustomUI` implementacji. W przeciwnym razie niestandardowa Wstążka mogą nie zachowywać się poprawnie. Jeśli musisz uruchomić kod, który inicjuje dodatku narzędzi VSTO dla programów, Dodaj kod, aby `ThisAddIn_Startup` programu obsługi zdarzeń.|
|`OnLoad`|Przypisuje <xref:Microsoft.Office.Core.IRibbonControl> parametr `Ribbon` pola. Aplikacje Microsoft Office wywołać tę metodę, gdy są one ładowane niestandardowa Wstążka. Można użyć tego pola, aby dynamicznie aktualizować niestandardowa Wstążka. Aby uzyskać więcej informacji, zobacz artykuł techniczny [Dostosowywanie interfejsu użytkownika wstążki pakietu Office (2007) dla deweloperów (część 1 z 3)](/previous-versions/office/developer/office-2007/aa338202(v=office.12)).|
|`GetResourceText`|Wywoływane przez `GetCustomUI` metodę, aby uzyskać zawartość pliku XML wstążki.|

## <a name="see-also"></a>Zobacz także
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
