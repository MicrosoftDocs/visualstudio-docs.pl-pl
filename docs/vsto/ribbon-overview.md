---
title: Omówienie wstążki
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 668517705caa7ba6baef0b85305bf4470bc3b26b
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985610"
---
# <a name="ribbon-overview"></a>Omówienie wstążki
  Wstążka jest sposobem organizowania powiązanych poleceń, aby ułatwić ich znalezienie. Polecenia są wyświetlane jako kontrolki na Wstążce. Kontrolki są zorganizowane w *grupy* wzdłuż górnej krawędzi okna aplikacji. Powiązane grupy są zorganizowane na kartach.

 Większość funkcji, do których uzyskano dostęp przy użyciu menu i pasków narzędzi we wcześniejszych wersjach systemu Microsoft Office, można teraz uzyskać dostęp za pomocą wstążki. Aby uzyskać więcej informacji, zapoznaj się z artykułem technicznym [Omówienie interfejsu użytkownika dla systemu 2007 Microsoft Office](/previous-versions/office/developer/office-2007/aa338198(v=office.12)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Dostosuj Wstążkę Microsoft Office
 Aby dostosować Wstążkę, Dodaj jeden z następujących elementów wstążki do projektu pakietu Office:

- **Wstążka (projektant graficzny)**

- **Wstążka (XML)**

  Na przykład aby dostosować Wstążkę programu Excel, Dodaj element wstążki do projektu dodatku VSTO dla programu Excel.

### <a name="ribbon-visual-designer-item"></a>Wstążka (projektant graficzny) — element
 Element **wstążka (projektant graficzny)** udostępnia zaawansowane narzędzia, które ułatwiają projektowanie i opracowywanie niestandardowej wstążki. Użyj **wstążki (projektant graficzny)** , aby dostosować Wstążkę w następujący sposób:

- Dodaj niestandardowe lub wbudowane karty do wstążki.

- Dodawanie grup niestandardowych do niestandardowej lub wbudowanej karty.

  > [!NOTE]
  > Wbudowana karta lub grupa jest taka, która już istnieje na Wstążce aplikacji Microsoft Office. Na przykład karta **dane** jest wbudowaną kartą w programie Excel. Grupa **połączeń** jest grupą wbudowaną na karcie **dane** .

- Dodaj niestandardowe kontrolki do grupy niestandardowej.

- Dodaj niestandardowe kontrolki do widoku Backstage.

  Aby uzyskać więcej informacji na temat dostosowywania wstążki przy użyciu elementu **wstążki (projektant graficzny)** , zobacz [Projektant wstążki](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Element wstążki (XML)
 Użyj elementu **wstążki (XML)** , jeśli chcesz dostosować Wstążkę w sposób, który nie jest obsługiwany przez **Wstążkę (projektant graficzny)** . Użyj elementu **wstążki (XML)** , aby dostosować Wstążkę w następujący sposób:

- Dodaj *wbudowane* grupy do niestandardowej karty lub karty wbudowanej.

- Dodaj wbudowane kontrolki do grupy niestandardowej.

- Dodaj niestandardowy kod, aby zastąpić procedury obsługi zdarzeń wbudowanych kontrolek.

- Dostosuj pasek narzędzi Szybki dostęp.

- Udostępnianie dostosowywania wstążki między dodatkiem VSTO przy użyciu kwalifikowanego identyfikatora.

  Aby uzyskać więcej informacji na temat dostosowywania wstążki przy użyciu elementu **wstążki (XML)** , zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Eksportowanie wstążki z projektanta wstążki do kodu XML wstążki
 Jeśli tworzysz Wstążkę przy użyciu projektanta wstążki, a następnie zdecydujesz, że chcesz dostosować Wstążkę w sposób, w jaki element **wstążka (projektant graficzny)** nie obsługuje, możesz wyeksportować Wstążkę do formatu XML.

 Program Visual Studio automatycznie tworzy element **wstążki (XML)** i wypełnia plik XML wstążki elementami i atrybutami dla każdej kontrolki na Wstążce.

 Nie wszystkie właściwości, które znajdują się w oknie **Właściwości** projektanta wstążki, są przenoszone do pliku XML wstążki.  Na przykład program Visual Studio nie eksportuje wartości właściwości **Image** lub **Text** . Oznacza to, że należy utworzyć metodę wywołania zwrotnego w pliku kodu wstążki wyeksportowanego projektu, aby przypisać obraz lub ustawić tekst kontrolki. Program Visual Studio nie generuje automatycznie metod wywołania zwrotnego w ramach procesu eksportu.

 Ponadto wszystkie niezmienione wartości właściwości domyślnych nie są wyświetlane w wynikach plików XML wstążki.

 Aby uzyskać więcej informacji o sposobach eksportowania wstążki do formatu XML, zobacz [How to: Export a wstążka z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="update-the-code"></a>Zaktualizuj kod
 Nowy plik kodu wstążki zostanie dodany do **Eksplorator rozwiązań**. Ten plik zawiera klasę XML wstążki. Należy utworzyć metody wywołania zwrotnego w regionie `Ribbon Callbacks` tej klasy, aby obsługiwać akcje użytkownika, takie jak kliknięcie przycisku. Przenieś swój kod z obsługi zdarzeń do tych metod wywołania zwrotnego i zmodyfikuj kod, aby działał z modelem programowania rozszerzalności wstążki (RibbonX). Aby uzyskać więcej informacji, zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

 Należy również dodać kod do klasy `ThisAddIn`, `ThisWorkbook`lub `ThisDocument`, która zastępuje metodę `CreateRibbonExtensibilityObject` i zwraca klasę XML wstążki do aplikacji pakietu Office.

 Aby uzyskać więcej informacji, zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Dodawanie wielu elementów wstążki do projektu
 Można dodać więcej niż jeden element wstążki do pojedynczego projektu. Jest to przydatne, jeśli chcesz wykonać jedną z następujących dwóch zadań:

- Tworzenie wstążki dla *inspektorów*programu Outlook. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Inspektor to okno otwierane, gdy użytkownicy wykonują określone zadania, takie jak tworzenie wiadomości e-mail.

- Wybierz Wstążkę, która ma być wyświetlana w czasie wykonywania.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Wybierz wstążki, które mają być wyświetlane w czasie wykonywania
 Ponieważ projekt może zawierać więcej niż jedną Wstążkę, można wybrać, która wstążka ma być wyświetlana w czasie wykonywania.

 Aby wybrać Wstążkę, która ma być wyświetlana w czasie wykonywania, Zastąp metodę `CreateRibbonExtensibilityObject` w klasie `ThisAddin`, `ThisWorkbook`lub `ThisDocument` projektu i zwróć Wstążkę, która ma zostać wyświetlona. Poniższy przykład sprawdza wartość pola o nazwie `myCondition` i zwraca odpowiednią Wstążkę.

> [!NOTE]
> Składnia używana w tym przykładzie zwraca Wstążkę, która została utworzona przy użyciu elementu **wstążki (projektant graficzny)** . Składnia zwracająca Wstążkę, która jest tworzona przy użyciu elementu **wstążki (XML)** , jest nieco inna. Aby uzyskać więcej informacji na temat zwracania elementu **wstążki (XML)** , zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

 Dodaj następujący kod:

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]

### <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)|Pokazuje, jak dostosować Wstążkę Microsoft Office aplikacji, dodać **Wstążkę (Visual Designer)** lub **Wstążkę (XML)** do projektu pakietu Office.|
|[Projektant wstążki](../vsto/ribbon-designer.md)|Opisuje, jak można użyć projektanta wstążki, aby dodać niestandardowe karty, grupy i kontrolki do wstążki aplikacji Microsoft Office.|
|[Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Pokazuje, jak utworzyć niestandardową kartę wstążki przy użyciu projektanta wstążki. Możesz użyć projektanta wstążki, aby dodać kontrolki i położenia ich na karcie niestandardowej.|
|[Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)|Zawiera omówienie modelu obiektów o jednoznacznie określonym typie, którego można użyć do pobierania i ustawiania właściwości formantów wstążki w czasie wykonywania.|
|[Przewodnik: aktualizowanie kontrolek na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Pokazuje, jak używać modelu obiektów wstążki do aktualizowania formantów na Wstążce po załadowaniu wstążki do aplikacji pakietu Office.|
|[Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Zawiera wskazówki dotyczące dostosowywania wstążki w programie Microsoft Office Outlook.|
|[Dostosowywanie wstążki dla programu InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Zawiera wskazówki dotyczące dostosowywania wstążki w programie Microsoft Office InfoPath.|
|[Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)|Pokazuje, jak pokazać, ukryć i zmodyfikować Wstążkę oraz umożliwić użytkownikom uruchamianie kodu z kontrolek w niestandardowym okienku zadań, okienku Akcje lub w regionie formularza programu Outlook.|
|[Instrukcje: zmiana położenia karty na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Pokazuje, jak zmienić kolejność kart na Wstążce.|
|[Instrukcje: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)|Pokazuje, jak dodać grupy i kontrolki do wbudowanej karty.|
|[Instrukcje: Dodawanie kontrolek do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Pokazuje, jak dodać kontrolki do menu, które jest otwierane po kliknięciu **pliku**.|
|[Instrukcje: Dodawanie uruchamiania okna dialogowego do grupy wstążki](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Pokazuje, jak dodać przycisk Uruchom okno dialogowe do każdej grupy na Wstążce.|
|[Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Pokazuje, jak dostosować Wstążkę w zaawansowanych sposobach, eksportując Wstążkę z projektanta do kodu XML wstążki.|
|[XML — wstążka](../vsto/ribbon-xml.md)|Wyjaśniono, jak można dostosować Wstążkę przy użyciu kodu XML wstążki.|
|[Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Pokazuje, jak utworzyć niestandardową kartę wstążki przy użyciu elementu **wstążki (XML)** .|
