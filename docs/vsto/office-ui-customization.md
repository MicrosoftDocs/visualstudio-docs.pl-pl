---
title: Dostosowywanie interfejsu użytkownika pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 052149783f93c1bf2f394be2fac9f6a51c9c0cf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977926"
---
# <a name="office-ui-customization"></a>Dostosowywanie interfejsu użytkownika pakietu Office
  Możesz dostosować interfejs użytkownika (UI) aplikacji pakietu Microsoft Office, przy użyciu narzędzi Office developer tools w programie Visual Studio. W tym temacie opisano funkcje interfejsu użytkownika, które można dostosować w następujących sekcjach:

- [Porównanie funkcji interfejsu użytkownika](#Comparison)

- [Okienka akcji i niestandardowych okienek zadań](#Actions)

- [Niestandardowy interfejs użytkownika wstążki.](#Ribbon)

- [Widok Backstage](#Backstage)

- [Regiony formularzy programu Outlook](#FormRegion)

- [Formanty w dokumentach](#Controls)

- [Menu skrótów](#Shortcut)

## <a name="Comparison"></a> Porównanie funkcji interfejsu użytkownika
 W poniższej tabeli porównano główne funkcje interfejsu użytkownika, które można dostosować w projektach programu Microsoft Office.

|Funkcja|Obsługiwane typy projektów|Obsługiwane aplikacje Microsoft Office|
|-------------|-----------------------------|---------------------------------------------|
|Okienko akcji|Dostosowania na poziomie dokumentów|Excel<br /><br /> Word|
|Niestandardowe okienka zadań|Dodatków narzędzi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|
|Niestandardowy interfejs użytkownika wstążki.|Dostosowania na poziomie dokumentów<br /><br /> Dodatków narzędzi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|
|Widok Backstage|Dostosowania na poziomie dokumentów<br /><br /> Dodatków narzędzi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|
|Regiony formularzy programu Outlook|Dodatków narzędzi VSTO|Outlook|
|Formanty w dokumentach|Dostosowania na poziomie dokumentów<br /><br /> Dodatków narzędzi VSTO|Excel<br /><br /> Word|
|Menu skrótów|Dostosowania na poziomie dokumentów<br /><br /> Dodatków narzędzi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|

## <a name="Actions"></a> Okienka akcji i niestandardowych okienek zadań
 Panele interfejsu użytkownika, które zwykle są zadokowane po jednej stronie okna aplikacji Microsoft Office są okienka zadań. Prawie wszystkie aplikacje Microsoft Office zawierają wbudowanego zadania okienka. Przykład okienka zadań to okienko zadań pomocy w programie Word.

 Narzędzi programistycznych pakietu Office w programie Visual Studio zawierają dwa różne sposoby dostosowywania okienka zadań:

- Możesz dodać okienek akcji do dostosowywania poziomie dokumentu. Domyślnie po prawej stronie aplikacji, po prawej stronie dokumentu zostanie wyświetlone okienko akcji. Jednak w okienku Akcje mogą być wyświetlane na od lewej górnej i dolnej części dokumentu.

- Dodatek narzędzi VSTO dla programów, można dodać niestandardowego okienka zadań. Użytkownikom można zadokować niestandardowych okienek zadań na różnych stronach w oknie aplikacji lub ich przeciągnij niestandardowych okienek zadań w dowolnej lokalizacji w oknie.

  Okienka akcji niestandardowych okienek zadań funkcję udostępnia i hostowanie wielu kontrolek, aby ułatwić użytkownikom wykonywanie zadań takich jak wprowadzanie danych. W porównaniu do grupy wstążek, okienka akcji i niestandardowych okienek zadań zapewnia znacznie większy obszar tekstu i formanty.

  Aby uzyskać więcej informacji na temat okienka akcji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md). Aby uzyskać więcej informacji na temat niestandardowych okienek zadań, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

## <a name="Ribbon"></a> Niestandardowy interfejs użytkownika wstążki.
 Można dostosować interfejsu użytkownika wstążki, aby udostępnić funkcje, które można dodać do aplikacji pakietu Office. Wstążka jest sposób organizowania powiązane polecenia (w formie formantów), aby były one łatwiej znaleźć. Możesz utworzyć własne karty Wstążki i grupy, aby zapewnić użytkownikom dostęp do funkcji, które oferują w rozwiązaniu. Większość funkcji, które były dostępne przy użyciu menu i pasków zadań we wcześniejszych wersjach systemu Microsoft Office może teraz uzyskiwać dostęp za pomocą wstążki.

 Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).

## <a name="Backstage"></a> Widok Backstage
 W aplikacjach pakietu Office, klikając **pliku** zostanie otwarta karta widoku Backstage. Widok Backstage zapewnia interfejs użytkownika, łączy zadania z poziomu plików i akcji, która zastępuje podobne funkcje dostępne z przycisk Microsoft Office w programie Microsoft Office system 2007. Widok Backstage jest całkowicie rozszerzalny za pomocą pliku XML.

 Program Visual Studio nie zapewnia projektanta lub interfejsów API do dostosowywania widoku Backstage. Jednak jeśli dodasz **wstążki (XML)** element XML do projektu pakietu Office, można dodać do pliku XML wstążki do dostosowywania widoku Backstage. Aby uzyskać więcej informacji na temat **wstążki (XML)** elementów, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).

 Aby uzyskać więcej informacji na temat dostosowywania widoku Backstage, zobacz [wprowadzenie do widoku widoku Backstage programu Office 2010 dla programistów](http://go.microsoft.com/fwlink/?LinkId=182189) i [dostosować widok widoku Backstage programu Office 2010 dla programistów](http://go.microsoft.com/fwlink/?LinkId=182188).

## <a name="FormRegion"></a> Regiony formularzy programu Outlook
 Użyj regionów formularzy w celu dodania funkcji niestandardowych do standardowych formularzy programu Microsoft Office Outlook. Można utworzyć regionów formularzy w, które rozszerzają dowolnego istniejącego formularza za pomocą dodatkowych pól lub kontrolek. Jeśli tworzysz nowy region formularza za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio, można użyć tylko formanty Windows Forms na region formularza. Jeśli importujesz regionu formularza zaprojektowanego w programie Outlook, można użyć tylko natywne kontrolki programu Outlook.

 Można utworzyć regionów formularzy, które zajmują różne obszary interfejsu użytkownika programu Outlook. Na przykład regionów formularzy w przylegającym są wyświetlane w dolnej części strony pierwszego formularza, a każdy sąsiednimi region formularza jest zwijany. Można również dodać regionu formularza oddzielny, która jest wyświetlana jako stronę pełnej dodatkowych formularzy i który może znajdować się na wszystkich istniejących formularza standardowego lub niestandardowego formularza.

 Aby uzyskać więcej informacji, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

## <a name="Controls"></a> Formanty w dokumentach
 Możesz dodać różne formanty dokumenty programu Word i arkusze programu Excel. Na przykład możesz chcieć dodać kontrolkę selektora daty do dokumentu, co użytkownik wpisz daty w standardowym formacie, albo umieść przycisku w arkuszach wysyłać dane do bazy danych.

 Podczas tworzenia projektów na poziomie dokumentu dla programu Excel lub Word, można użyć projektanta programu Visual Studio, aby dodać formanty do dokumentu lub skoroszytu w projekcie w czasie projektowania lub można programowo dodać formanty w czasie wykonywania. Podczas tworzenia projektów dodatku VSTO dla programu Excel lub Word, można programowo dodawać formanty, otwórz dokument lub skoroszyt w czasie wykonywania.

 Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md) i [Windows forms, formanty na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="Shortcut"></a> Menu skrótów
 Menu skrótów pojawia się po kliknięciu prawym przyciskiem myszy w oknie aplikacji lub dokumentu. Możesz ustawić menu skrótów, po wystąpieniu zdarzenia, takie jak kiedy użytkownik kliknie prawym przyciskiem myszy dokumentu, skoroszytu lub kontrolki hosta. Liczba różnych menu poleceń lub kontrolek można dodać do menu skrótów. Tworzenie menu skrótów za pomocą pliku XML. Jeśli dodasz **wstążki (XML)** element XML do projektu pakietu Office, można dodać do pliku XML wstążki, aby utworzyć menu skrótów. Aby uzyskać więcej informacji na temat za pomocą języka XML, aby utworzyć menu skrótów, zobacz [jak: Dodawanie poleceń do menu skrótów](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="see-also"></a>Zobacz także
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Windows forms, formanty na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Użyj kontrolek WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Instrukcje: Pokazywanie karty dewelopera na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [Instrukcje: Pokaż błędy interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Przewodnik: Zbieranie danych za pomocą formularza Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
