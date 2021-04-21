---
title: Wstążka — omówienie
description: Dowiedz się, jak wstążka umożliwia organizowanie powiązanych poleceń, aby ułatwić ich znajdowanie i sposób, w jaki polecenia są wyświetlane jako kontrolki na wstążce.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8920c8a402b4566cf95bb74626171cca833d32de
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825553"
---
# <a name="ribbon-overview"></a>Wstążka — omówienie
  Wstążka to sposób organizowania powiązanych poleceń, aby ułatwić ich znajdowanie. Polecenia są wyświetlane jako kontrolki na wstążce. Kontrolki są zorganizowane *w grupy* wzdłuż poziomego paska na górnej krawędzi okna aplikacji. Powiązane grupy są zorganizowane na kartach.

 Większość funkcji, do których uzyskano dostęp przy użyciu menu i pasków narzędzi we wcześniejszych wersjach systemu Microsoft Office, jest teraz dostępna za pomocą wstążki. Aby uzyskać więcej informacji, zobacz artykuł techniczny [Developer overview of the user interface for the 2007 Microsoft Office system](/previous-versions/office/developer/office-2007/aa338198(v=office.12)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Dostosowywanie Microsoft Office danych
 Aby dostosować wstążkę, dodaj do projektu pakietu Office jeden z następujących elementów wstążki:

- **Wstążka (Projektant wizualny)**

- **Wstążka (XML)**

  Aby na przykład dostosować wstążkę programu Excel, dodaj element wstążki do projektu dodatku VSTO programu Excel.

### <a name="ribbon-visual-designer-item"></a>Element wstążki (Projektant wizualny)
 Element **Wstążka (Projektant wizualny)** zawiera zaawansowane narzędzia, które ułatwiają projektowanie i opracowywanie niestandardowej wstążki. Element Wstążki **(Projektant wizualny)** umożliwia dostosowanie wstążki w następujący sposób:

- Dodawanie kart niestandardowych lub wbudowanych do wstążki.

- Dodawanie grup niestandardowych do karty niestandardowej lub wbudowanej.

  > [!NOTE]
  > Wbudowana karta lub grupa to taka, która już istnieje na wstążce Microsoft Office aplikacji. Na przykład karta **Dane jest** wbudowaną kartą w programie Excel. Grupa **Połączenia** jest wbudowaną grupą na **karcie** Dane.

- Dodawanie kontrolek niestandardowych do grupy niestandardowej.

- Dodaj kontrolki niestandardowe do widoku Backstage.

  Aby uzyskać więcej informacji na temat dostosowywania wstążki przy użyciu elementu Wstążki **(Projektant** wizualizacji), zobacz [Projektant wstążki](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Element wstążki (XML)
 Użyj elementu **Wstążki (XML),** jeśli chcesz dostosować wstążkę w sposób, który nie jest obsługiwany przez element Wstążki **(Projektant wizualny).** Użyj elementu **Wstążki (XML),** aby dostosować wstążkę w następujący sposób:

- Dodawanie *wbudowanych grup* do karty niestandardowej lub karty wbudowanej.

- Dodawanie wbudowanych kontrolek do grupy niestandardowej.

- Dodaj kod niestandardowy, aby przesłonić procedury obsługi zdarzeń wbudowanych kontrolek.

- Dostosuj pasek narzędzi Szybki dostęp.

- Udostępnianie dostosowania wstążki między dodatku VSTO przy użyciu kwalifikowanego identyfikatora.

  Aby uzyskać więcej informacji na temat dostosowywania wstążki przy użyciu elementu **wstążki (XML),** zobacz [Xml wstążki](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Eksportowanie wstążki z Projektanta wstążki do pliku XML wstążki
 Jeśli utworzysz wstążkę przy użyciu Projektanta wstążki, a następnie zdecydujesz, że chcesz dostosować wstążkę w sposób, który nie jest przez element Wstążki **(Visual Designer),** możesz wyeksportować wstążkę do formatu XML.

 Visual Studio automatycznie tworzy element wstążki **(XML)** i wypełnia plik XML wstążki elementami i atrybutami dla każdej kontrolki na wstążce.

 Nie wszystkie właściwości, które znajdują się w **oknie** Właściwości Projektanta wstążki, są przenoszone do pliku XML wstążki.  Na przykład Visual Studio nie eksportuje wartości właściwości  Image **lub** Text. Wynika to z tego, że należy utworzyć metodę wywołania zwrotnego w pliku kodu wstążki wyeksportowanego projektu, aby przypisać obraz lub ustawić tekst kontrolki. Visual Studio nie generuje automatycznie metod wywołania zwrotnego w ramach procesu eksportowania.

 Ponadto wszelkie niezmienione domyślne wartości właściwości nie są wyświetlane w wynikowym pliku XML wstążki.

 Aby uzyskać więcej informacji na temat eksportowania wstążki do formatu XML, zobacz Jak wyeksportować wstążkę z Projektanta wstążki [do pliku XML wstążki.](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)

### <a name="update-the-code"></a>Aktualizacja kodu
 Nowy plik kodu wstążki jest dodawany **do** Eksplorator rozwiązań . Ten plik zawiera klasę XML wstążki. Należy utworzyć metody wywołania zwrotnego w regionie tej klasy, aby obsługiwać akcje użytkownika, takie `Ribbon Callbacks` jak kliknięcie przycisku. Przenieś kod z programów obsługi zdarzeń do tych metod wywołania zwrotnego i zmodyfikuj go, aby działał z modelem programowania rozszerzalności wstążki (RibbonX). Aby uzyskać więcej informacji, zobacz [Xml wstążki](../vsto/ribbon-xml.md).

 Należy również dodać kod do klasy , lub , który zastępuje metodę i zwraca klasę XML wstążki `ThisAddIn` `ThisWorkbook` do aplikacji pakietu `ThisDocument` `CreateRibbonExtensibilityObject` Office.

 Aby uzyskać więcej informacji, zobacz [Xml wstążki](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Dodawanie wielu elementów wstążki do projektu
 Do pojedynczego projektu można dodać więcej niż jeden element wstążki. Jest to przydatne, jeśli chcesz wykonać jeden z następujących dwóch zadań:

- Utwórz wstążki dla inspektorów *programu* Outlook. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wstążki dla programu Outlook.](../vsto/customizing-a-ribbon-for-outlook.md)

    > [!NOTE]
    > Inspektor to okno, które jest otwierane, gdy użytkownicy wykonują pewne zadania, takie jak tworzenie wiadomości e-mail.

- Wybierz wstążkę do wyświetlenia w czasie uruchamiania.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Wybieranie wstążek do wyświetlenia w czasie uruchamiania
 Ponieważ projekt może zawierać więcej niż jedną wstążkę, możesz wybrać wstążkę do wyświetlenia w czasie uruchamiania.

 Aby wybrać wstążkę do wyświetlenia w czasie uruchamiania, zastąp metodę w klasie , lub projektu i zwróć wstążkę, którą `CreateRibbonExtensibilityObject` `ThisAddin` chcesz `ThisWorkbook` `ThisDocument` wyświetlić. Poniższy przykład sprawdza wartość pola o nazwie `myCondition` i zwraca odpowiednią wstążkę.

> [!NOTE]
> Składnia używana w tym przykładzie zwraca wstążkę, która została utworzona przy użyciu elementu **Wstążki (Visual Designer).** Składnia zwracania wstążki utworzonej przy użyciu elementu wstążki **(XML)** jest nieco inna. Aby uzyskać więcej informacji na temat zwracania elementu wstążki **(XML),** zobacz [Xml wstążki](../vsto/ribbon-xml.md).

 Dodaj następujący kod:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs" id="Snippet1":::

### <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)|Pokazuje, jak dostosować wstążkę aplikacji Microsoft Office, dodać element wstążki **(Visual Designer)** lub wstążki **(XML)** do projektu pakietu Office.|
|[Projektant wstążki](../vsto/ribbon-designer.md)|Opisuje sposób używania Projektanta wstążki do dodawania niestandardowych kart, grup i kontrolek do wstążki Microsoft Office aplikacji.|
|[Przewodnik: tworzenie karty niestandardowej przy użyciu Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Pokazuje, jak utworzyć niestandardową kartę wstążki przy użyciu Projektanta wstążki. Za pomocą Projektanta wstążki można dodawać kontrolki i pozycjonować je na karcie niestandardowej.|
|[Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)|Zawiera omówienie silnie typowego modelu obiektów, za pomocą których można pobrać i ustawić właściwości kontrolek wstążki w czasie uruchamiania.|
|[Przewodnik: aktualizowanie kontrolek na wstążce w czasie uruchamiania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Pokazuje, jak za pomocą modelu obiektów wstążki zaktualizować kontrolki na wstążce po załadowaniu wstążki do aplikacji pakietu Office.|
|[Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Zawiera wskazówki dotyczące dostosowywania wstążki w programie Microsoft Office Outlook.|
|[Dostosowywanie wstążki dla programu InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Zawiera wskazówki dotyczące dostosowywania wstążki w programie Microsoft Office InfoPath.|
|[Uzyskiwanie dostępu do wstążki w czasie uruchamiania](../vsto/accessing-the-ribbon-at-run-time.md)|Przedstawia sposób pokazywania, ukrywania i modyfikowania wstążki oraz umożliwia użytkownikom uruchamianie kodu z kontrolek w niestandardowym okienku zadań, okienku akcji lub obszarze formularza programu Outlook.|
|[Jak zmienić położenie karty na wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Pokazuje, jak zmienić kolejność kart na wstążce.|
|[How to: Customize a built-in tab (2017: Dostosowywanie wbudowanej karty)](../vsto/how-to-customize-a-built-in-tab.md)|Pokazuje sposób dodawania grup i kontrolek do karty wbudowanej.|
|[Jak dodać kontrolki do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Pokazuje sposób dodawania kontrolek do menu otwieranych po kliknięciu **pliku**.|
|[Jak dodać uruchamianie okna dialogowego do grupy wstążki](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Pokazuje, aby dodać uruchamianie okna dialogowego do dowolnej grupy na wstążce.|
|[How to: Export a ribbon from the Ribbon Designer to Ribbon XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Przedstawia sposób zaawansowanego dostosowywania wstążki przez wyeksportowanie wstążki z projektanta do pliku XML wstążki.|
|[XML — Wstążka](../vsto/ribbon-xml.md)|Wyjaśnia, jak można dostosować wstążkę przy użyciu xml wstążki.|
|[Przewodnik: tworzenie karty niestandardowej przy użyciu Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Pokazuje, jak utworzyć niestandardową kartę wstążki przy użyciu **elementu wstążki (XML).**|
