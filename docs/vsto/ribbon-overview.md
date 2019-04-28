---
title: Wstążka — omówienie
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
ms.openlocfilehash: 8697a49c57840d358eeaa597fe984b6671958b09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446970"
---
# <a name="ribbon-overview"></a>Wstążka — omówienie
  Wstążka jest sposób organizowania powiązane polecenia, aby były one łatwiej znaleźć. Polecenia są wyświetlane jako formanty na Wstążce. Formanty są zorganizowane w *grup* wzdłuż poziomy pasek do górnej krawędzi okna aplikacji. Powiązane grupy są zorganizowane na kartach.

 Większość funkcji, które były dostępne przy użyciu menu i pasków zadań we wcześniejszych wersjach systemu Microsoft Office może teraz uzyskiwać dostęp za pomocą wstążki. Aby uzyskać więcej informacji, zobacz artykuł techniczny [omówienie dla deweloperów interfejsu użytkownika pakietu Microsoft Office system 2007](http://go.microsoft.com/fwlink/?LinkID=70860).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Dostosowywanie Wstążki pakietu Microsoft Office
 Dostosowywanie Wstążki, Dodaj jedną z następujących elementów wstążki do projektu pakietu Office:

- **Wstążka (Projektant graficzny)**

- **Wstążka (XML)**

  Na przykład aby dostosować na wstążce programu Excel, Dodaj element wstążki do projektu dodatku narzędzi VSTO programu Excel.

### <a name="ribbon-visual-designer-item"></a>Element wstążki (Projektant graficzny)
 **Wstążka (Projektant graficzny)** elementu udostępnia zaawansowane narzędzia, które ułatwiają projektowanie i tworzenie niestandardowych wstążki. Użyj **Wstążka (Projektant graficzny)** elementu w celu dostosowania wstążki w następujący sposób:

- Dodaj niestandardowe i wbudowane karty do wstążki.

- Dodawanie niestandardowych grup niestandardowych lub wbudowane karty.

  > [!NOTE]
  > Wbudowanej karty lub grupy to taki, który już istnieje na Wstążce aplikacji Microsoft Office. Na przykład **danych** karty to karta wbudowana w programie Excel. **Połączeń** grupy Grupa jest wbudowana w **danych** kartę.

- Dodawanie niestandardowych formantów do grupy niestandardowej.

- Dodawanie niestandardowych formantów do widoku Backstage.

  Aby uzyskać więcej informacji o dostosowywaniu wstążki przy użyciu **Wstążka (Projektant graficzny)** elementu, zobacz [projektanta wstążki](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Element wstążki (XML)
 Użyj **wstążki (XML)** elementu, jeśli chcesz dostosowania wstążki w taki sposób, że nie jest obsługiwana przez **Wstążka (Projektant graficzny)** elementu. Użyj **wstążki (XML)** elementu w celu dostosowania wstążki w następujący sposób:

- Dodaj *wbudowanych* grup, do niestandardowej karty lub wbudowanej karty.

- Dodawanie wbudowanych formantów do grupy niestandardowe.

- Dodawanie kodu niestandardowego, aby zastąpić procedury obsługi zdarzeń formantów wbudowanych.

- Dostosowywanie paska narzędzi Szybki dostęp.

- Udostępnianie dostosowania wstążki w między dodatku narzędzi VSTO za pomocą kwalifikowanego identyfikatora.

  Aby uzyskać więcej informacji o dostosowywaniu wstążki przy użyciu **wstążki (XML)** elementu, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Eksportowanie wstążki z projektanta wstążki do XML wstążki
 Jeśli tworzenie wstążki przy użyciu projektanta wstążki, a następnie zdecydować, chcesz dostosowania wstążki w sposób, **Wstążka (Projektant graficzny)** element nie obsługuje, można wyeksportować wstążki do XML.

 Program Visual Studio automatycznie tworzy **wstążki (XML)** element i wypełnia pliku XML wstążki przy użyciu elementów i atrybutów dla każdego formantu na Wstążce.

 Nie wszystkie właściwości, które znajdują się w **właściwości** okna projektanta wstążki są przekazywane do pliku XML wstążki.  Na przykład programu Visual Studio nie eksportuje wartości **obraz** lub **tekstu** właściwości. To, ponieważ należy utworzyć metodę wywołania zwrotnego w pliku kodu wstążki wyeksportowanego projekt, aby przypisać obrazu lub ustawianie tekstu w kontrolce. Program Visual Studio nie generuje automatycznie metody wywołania zwrotnego w ramach procesu eksportu.

 Ponadto wszelkie domyślne bez zmian wartości właściwości nie są wyświetlane w powstałym pliku XML wstążki.

 Aby uzyskać więcej informacji o sposobie eksportowania wstążki do XML, zobacz [jak: Eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="update-the-code"></a>Aktualizowanie kodu
 Zostanie dodany nowy plik kodu wstążki, aby **Eksploratora rozwiązań**. Ten plik zawiera klasę kodu XML wstążki. Należy utworzyć w metody wywołania zwrotnego `Ribbon Callbacks` tej klasy, aby obsłużyć akcje użytkownika, takie jak kliknięcie przycisku. Przenieś swój kod z procedur obsługi zdarzeń do tych metod wywołania zwrotnego i zmodyfikuj kod do działania z modelu programowania rozszerzalności wstążki (RibbonX). Aby uzyskać więcej informacji, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).

 Musisz również dodać kod, aby `ThisAddIn`, `ThisWorkbook`, lub `ThisDocument` klasę, która zastępuje `CreateRibbonExtensibilityObject` metodę i zwraca XML wstążki klasy do aplikacji pakietu Office.

 Aby uzyskać więcej informacji, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Dodawanie wielu elementów wstążki do projektu
 Możesz dodać więcej niż jeden element wstążki do pojedynczego projektu. Jest to przydatne, jeśli chcesz wykonać jedną z poniższych czynności:

- Tworzenie Wstążki programu Outlook *inspektorzy*. Aby uzyskać więcej informacji, zobacz [Dostosuj Wstążkę dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Inspektor jest oknem, która zostanie otwarta, gdy użytkownicy wykonają pewnych zadań, takich jak tworzenie wiadomości e-mail.

- Wybierz, które wstążki do wyświetlenia w czasie wykonywania.

### <a name="select-which-ribbons-to-display-at-runtime"></a>Wybierz, które taśmy do wyświetlenia w czasie wykonywania
 Projekt może zawierać więcej niż jeden wstążki, można wybrać, które wstążki do wyświetlenia w czasie wykonywania.

 Aby wybrać wstążki do wyświetlenia w czasie wykonywania, należy zastąpić `CreateRibbonExtensibilityObject` method in Class metoda `ThisAddin`, `ThisWorkbook`, lub `ThisDocument` klasy projektu i zwrócenia wstążki, który chcesz wyświetlić. Poniższy przykład sprawdza wartość pola o nazwie `myCondition` i zwraca odpowiednią wstążki.

> [!NOTE]
> Składnią używaną w tym przykładzie zwraca wstążki, który został utworzony przy użyciu **Wstążka (Projektant graficzny)** elementu. Składnia służąca do zwracania wstążki, która jest tworzona przy użyciu **wstążki (XML)** elementu jest nieco inne. Aby uzyskać więcej informacji na temat zwracanie **wstążki (XML)** elementu, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).

 Dodaj następujący kod:

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]

### <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)|Pokazuje, jak Dostosowywanie Wstążki aplikacji pakietu Microsoft Office, dodawanie **Wstążka (Projektant graficzny)** lub **wstążki (XML)** elementu do projektu programu pakietu Office.|
|[Projektant wstążki](../vsto/ribbon-designer.md)|W tym artykule opisano, jak można użyć projektanta wstążki można dodać niestandardowe karty, grupy i formanty do Wstążki aplikacji pakietu Microsoft Office.|
|[Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Dowiesz się, jak utworzyć niestandardowe karty wstążki przy użyciu projektanta wstążki. Projektant wstążki umożliwia dodawanie i ustawianie formantów na karcie niestandardowe.|
|[Model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md)|Omówienie modelu silnie typizowany obiekt, który służy do pobierania i ustawiania właściwości formantów wstążki w czasie wykonywania.|
|[Przewodnik: Aktualizowanie formantów na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Pokazuje, jak aktualizowanie formantów na Wstążce po załadowaniu wstążki do aplikacji pakietu Office za pomocą modelu obiektów wstążki.|
|[Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Zawiera wskazówki dotyczące dostosowywania wstążki w programie Microsoft Office Outlook.|
|[Dostosowywanie wstążki do InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Zawiera wskazówki dotyczące dostosowywania wstążki w programie Microsoft Office InfoPath.|
|[Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)|Pokazuje, jak pokazywanie, ukrywanie, modyfikowania Wstążki i umożliwiają użytkownikom uruchomić kod z kontrolek w niestandardowego okienka zadań, okienka akcji lub region formularza programu Outlook.|
|[Instrukcje: Zmiana położenia zakładki na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Pokazuje, jak zmiana kolejności kart na Wstążce.|
|[Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)|Pokazuje, jak dodać grupy i formanty do wbudowanej karty.|
|[Instrukcje: Dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Pokazuje, jak dodać formanty do menu otwieranego po kliknięciu **pliku**.|
|[Instrukcje: Dodaj przycisk Uruchom okno dialogowe do grupy wstążki](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Pokazuje, jak dodać przycisk Uruchom okno dialogowe z żadną grupą na Wstążce.|
|[Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Pokazuje, jak w celu dostosowania wstążki w zaawansowanych sposobów eksportując przy użyciu projektanta wstążki do XML wstążki.|
|[XML — wstążka](../vsto/ribbon-xml.md)|W tym artykule wyjaśniono, w jaki sposób dostosować wstążki za pomocą XML wstążki.|
|[Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Pokazuje, jak utworzyć niestandardową kartę Wstążki przy użyciu **wstążki (XML)** elementu.|
