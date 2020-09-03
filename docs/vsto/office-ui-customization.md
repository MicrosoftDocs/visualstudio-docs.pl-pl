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
ms.openlocfilehash: 257f87aedf5d4337e81fb6f251cc8df07f4e577c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88041067"
---
# <a name="office-ui-customization"></a>Dostosowywanie interfejsu użytkownika pakietu Office
  Interfejs użytkownika (UI) aplikacji Microsoft Office można dostosować przy użyciu narzędzi Office Developer Tools w programie Visual Studio. W tym temacie opisano funkcje interfejsu użytkownika, które można dostosować w następujących sekcjach:

- [Porównanie funkcji interfejsu użytkownika](#Comparison)

- [Okienka akcji i niestandardowe okienka zadań](#Actions)

- [Niestandardowy interfejs użytkownika wstążki](#Ribbon)

- [Widok Backstage](#Backstage)

- [Regiony formularzy programu Outlook](#FormRegion)

- [Kontrolki dokumentów](#Controls)

- [Menu skrótów](#Shortcut)

## <a name="comparison-of-ui-features"></a><a name="Comparison"></a> Porównanie funkcji interfejsu użytkownika
 Poniższa tabela zawiera porównanie głównych funkcji interfejsu użytkownika, które można dostosować w projektach Microsoft Office.

|Cechy|Obsługiwane typy projektów|Obsługiwane Microsoft Office aplikacje|
|-------------|-----------------------------|---------------------------------------------|
|Okienko akcje|Dostosowania na poziomie dokumentów|Excel<br /><br /> Word|
|Niestandardowe okienka zadań|Dodatki narzędzi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|Niestandardowy interfejs użytkownika wstążki|Dostosowania na poziomie dokumentów<br /><br /> Dodatki narzędzi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Widok Backstage|Dostosowania na poziomie dokumentów<br /><br /> Dodatki narzędzi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Regiony formularzy programu Outlook|Dodatki narzędzi VSTO|Outlook|
|Kontrolki dokumentów|Dostosowania na poziomie dokumentów<br /><br /> Dodatki narzędzi VSTO|Excel<br /><br /> Word|
|Menu skrótów|Dostosowania na poziomie dokumentów<br /><br /> Dodatki narzędzi VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|

## <a name="actions-panes-and-custom-task-panes"></a><a name="Actions"></a> Okienka akcji i niestandardowe okienka zadań
 Okienka zadań to panele interfejsu użytkownika, które zwykle są zadokowane po jednej stronie okna w aplikacji Microsoft Office. Prawie wszystkie Microsoft Office aplikacje obejmują wbudowane okienka zadań. Przykładem okienka zadań jest okienko zadań pomoc w programie Word.

 Narzędzia programistyczne pakietu Office w programie Visual Studio oferują dwa różne sposoby dostosowywania okienka zadań:

- Okienko akcji można dodać do dostosowania na poziomie dokumentu. Domyślnie okienko akcje jest wyświetlane po prawej stronie aplikacji z prawej strony dokumentu. Jednak okienko akcje może być również wyświetlane w lewej, górnej lub dolnej części dokumentu.

- Możesz dodać niestandardowe okienko zadań do dodatku narzędzi VSTO. Użytkownicy mogą dokować niestandardowe okienka zadań na różnych stronach okna aplikacji lub przeciągać niestandardowe okienka zadań do dowolnej lokalizacji w oknie.

  Okienka akcji i niestandardowe okienka zadań zapewniają funkcje, udostępniając różne kontrolki, które ułatwiają użytkownikom wykonywanie zadań, takich jak wprowadzanie danych. W porównaniu z grupą wstążki okienka akcji i niestandardowe okienka zadań zapewniają znacznie większy obszar do uwzględnienia tekstu i kontrolek.

  Aby uzyskać więcej informacji na temat okienek akcji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md). Aby uzyskać więcej informacji na temat niestandardowych okienek zadań, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

## <a name="custom-ribbon-ui"></a><a name="Ribbon"></a> Niestandardowy interfejs użytkownika wstążki
 Interfejs użytkownika wstążki można dostosować w taki sposób, aby uwidaczniał funkcje dodawane do aplikacji w pakiecie Office. Wstążka jest sposobem organizowania powiązanych poleceń (w formie kontrolek), aby ułatwić ich znalezienie. Możesz utworzyć własne karty wstążki i grupy, aby zapewnić użytkownikom dostęp do funkcji udostępnianych w rozwiązaniu. Większość funkcji, do których uzyskano dostęp przy użyciu menu i pasków narzędzi we wcześniejszych wersjach systemu Microsoft Office, można teraz uzyskać dostęp za pomocą wstążki.

 Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

## <a name="backstage-view"></a><a name="Backstage"></a> Widok Backstage
 W aplikacjach pakietu Office kliknięcie karty **plik** spowoduje otwarcie widoku Backstage. Widok Backstage udostępnia interfejs użytkownika, który łączy zadania i akcje na poziomie plików, a także zastępuje podobne funkcje dostępne na przycisku Microsoft Office w systemie Microsoft Office 2007. Widok Backstage jest w pełni rozszerzalny przy użyciu XML.

 Program Visual Studio nie udostępnia projektanta ani interfejsów API do dostosowywania widoku Backstage. Jeśli jednak dodasz element **wstążki (XML)** do projektu pakietu Office, możesz dodać kod XML do pliku XML wstążki, aby dostosować widok Backstage. Aby uzyskać więcej informacji na temat elementów **wstążki (XML)** , zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

 Aby uzyskać więcej informacji na temat dostosowywania widoku Backstage, zobacz [wprowadzenie do widoku Backstage pakietu office 2010 dla deweloperów](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) i [Dostosuj widok backstage pakietu Office 2010 dla deweloperów](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

## <a name="outlook-form-regions"></a><a name="FormRegion"></a> Regiony formularzy programu Outlook
 Za pomocą regionów formularza można dodawać niestandardowe funkcje do standardowych formularzy programu Outlook Microsoft Office. Można tworzyć regiony formularzy, które poszerzają wszelkie istniejące formularze z dodatkowymi polami lub kontrolkami. Jeśli tworzysz nowy region formularza przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, możesz użyć tylko formantów Windows Forms w regionie formularza. W przypadku zaimportowania regionu formularza, który został zaprojektowany w programie Outlook, można używać tylko natywnych kontrolek programu Outlook.

 Można tworzyć regiony formularzy, które zajmują różne obszary interfejsu użytkownika programu Outlook. Na przykład sąsiadujące regiony formularza są wyświetlane u dołu pierwszej strony formularza, a każdy region przylegających formularzy jest zwijany. Możesz również dodać osobny region formularza, który jest wyświetlany jako pełna dodatkowa strona formularza i który może być wyświetlany na dowolnym istniejącym formularzu standardowym lub formularzu niestandardowym.

 Aby uzyskać więcej informacji, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="controls-on-documents"></a><a name="Controls"></a> Kontrolki dokumentów
 Można dodać różne kontrolki do dokumentów programu Word i arkuszy programu Excel. Na przykład możesz chcieć dodać kontrolkę selektora daty do dokumentu, aby użytkownik mógł wprowadzić daty w formacie standardowym, lub umieścić przycisk w arkuszu, aby wysłać dane do bazy danych.

 Podczas opracowywania projektów na poziomie dokumentu dla programu Excel lub Word, można użyć projektanta programu Visual Studio, aby dodać kontrolki do dokumentu lub skoroszytu w projekcie w czasie projektowania lub można programowo dodać kontrolki w czasie wykonywania. Podczas tworzenia projektów dodatku VSTO dla programu Excel lub Word, można programowo dodać kontrolki do dowolnego otwartego dokumentu lub skoroszytu w czasie wykonywania.

 Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md) oraz [kontrolek Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="shortcut-menus"></a><a name="Shortcut"></a> Menu skrótów
 Menu skrótów pojawia się po kliknięciu prawym przyciskiem myszy w oknie dokumentu lub aplikacji. Można ustawić menu skrótów, które ma być wyświetlane po wystąpieniu zdarzenia, na przykład gdy użytkownik kliknie prawym przyciskiem myszy dokument, skoroszyt lub formant hosta. Do menu skrótów można dodać wiele różnych poleceń menu lub kontrolek. Utwórz menu skrótów za pomocą języka XML. Jeśli dodasz element **wstążki (XML)** do projektu pakietu Office, możesz dodać kod XML do pliku XML wstążki, aby utworzyć menu skrótów. Aby uzyskać więcej informacji na temat tworzenia menu skrótów przy użyciu języka XML, zobacz [jak: Dodawanie poleceń do menu skrótów](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Kontrolki formularzy Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Przegląd okienka Akcje](../vsto/actions-pane-overview.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Korzystanie z formantów WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Instrukcje: pokazywanie karty dewelopera na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [Instrukcje: pokazywanie błędów interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Przewodnik: zbieranie danych przy użyciu formularza systemu Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
