---
title: Niestandardowe okienka zadań
description: Dowiedz się, że niestandardowe okienka zadań zapewniają sposób tworzenia własnego okienka zadań i zapewniają użytkownikom znany interfejs dostępu do funkcji rozwiązania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6c35d963b426fe24a43bef24617f79c042c272e9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828166"
---
# <a name="custom-task-panes"></a>Niestandardowe okienka zadań
  Okienka zadań to panele interfejsu użytkownika, które są zwykle zadokowane do jednej strony okna w Microsoft Office aplikacji. Niestandardowe okienka zadań zapewniają sposób tworzenia własnego okienka zadań i udostępniania użytkownikom znanego interfejsu w celu uzyskania dostępu do funkcji rozwiązania. Na przykład interfejs może zawierać kontrolki, które uruchamiają kod w celu modyfikowania dokumentów lub wyświetlania danych ze źródła danych.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Niestandardowe okienko zadań różni się od okienka akcji. Okienko akcji jest częścią dostosowań na poziomie dokumentu dla programu Microsoft Office Word i Microsoft Office Excel. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

## <a name="benefits-of-custom-task-panes"></a>Zalety niestandardowych okienek zadań
 Niestandardowe okienka zadań umożliwiają zintegrowanie funkcji ze znanym interfejsem użytkownika. Niestandardowe okienko zadań można szybko utworzyć przy użyciu Visual Studio zadań.

### <a name="familiar-user-interface"></a>Znany interfejs użytkownika
 Użytkownicy aplikacji w systemie Microsoft Office są już zaznajomieni z używaniem okienek zadań, takich jak okienko zadań Style i **formatowanie** w programie Word. Niestandardowe okienka zadań zachowują się jak inne okienka zadań w Microsoft Office systemu. Użytkownicy mogą dokować niestandardowe okienka zadań do różnych stron okna aplikacji lub przeciągać niestandardowe okienka zadań do dowolnej lokalizacji w oknie. Można utworzyć dodatek narzędzi VSTO, który wyświetla wiele niestandardowych okienek zadań w tym samym czasie, a użytkownicy mogą kontrolować poszczególne okienka zadań.

### <a name="windows-forms-support"></a>Obsługa formularzy systemu Windows
 Interfejs użytkownika niestandardowego okienka zadań, który można utworzyć przy użyciu narzędzi deweloperskie pakietu Office w programie Visual Studio jest oparty na Windows Forms kontroli. Znajomy interfejs Projektant formularzy systemu Windows umożliwia zaprojektowanie interfejsu użytkownika dla niestandardowego okienka zadań. Obsługę powiązań danych można również użyć w Windows Forms, aby powiązać źródło danych z kontrolkami w okienku zadań.

## <a name="create-a-custom-task-pane"></a>Tworzenie niestandardowego okienka zadań
 Podstawowe niestandardowe okienko zadań można utworzyć w dwóch krokach:

1. Utwórz interfejs użytkownika dla niestandardowego okienka zadań, dodając Windows Forms do <xref:System.Windows.Forms.UserControl> obiektu.

2. W okienku zadań niestandardowych należy utworzyć wystąpienia, przekazując kontrolkę użytkownika <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> do obiektu w dodatku narzędzi VSTO. Ta kolekcja zwraca nowy obiekt, który umożliwia modyfikowanie wyglądu okienka zadań i <xref:Microsoft.Office.Tools.CustomTaskPane> reagowanie na zdarzenia użytkownika.

   Aby uzyskać więcej informacji, [zobacz Jak dodać niestandardowe okienko zadań do aplikacji.](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)

### <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika
 Wszystkie niestandardowe okienka zadań tworzone przy użyciu narzędzi programistyczych pakietu Office Visual Studio zawierają <xref:System.Windows.Forms.UserControl> obiekt . Ta kontrolka użytkownika udostępnia interfejs użytkownika niestandardowego okienka zadań. Kontrolkę użytkownika można utworzyć w czasie projektowania lub w czasie uruchamiania. Jeśli tworzysz kontrolkę użytkownika w czasie projektowania, możesz użyć Projektant formularzy systemu Windows, aby skonstruować interfejs użytkownika okienka zadań.

### <a name="instantiate-the-custom-task-pane"></a>Wystąpienia niestandardowego okienka zadań
 Po utworzeniu kontrolki użytkownika zawierającej interfejs użytkownika niestandardowego okienka zadań należy utworzyć wystąpienia <xref:Microsoft.Office.Tools.CustomTaskPane> . W tym celu przekaż kontrolkę użytkownika do dodatku <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> VSTO, wywołując jedną z <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metod. Ta kolekcja jest `CustomTaskPanes` ujmowany jako pole klasy `ThisAddIn` . Poniższy przykład kodu jest przeznaczony do uruchamiania z `ThisAddIn` klasy .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

 Metody <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> zwracają nowy obiekt <xref:Microsoft.Office.Tools.CustomTaskPane> . Ten obiekt umożliwia modyfikowanie wyglądu okienka zadań i reagowanie na zdarzenia użytkownika.

### <a name="control-the-task-pane-in-multiple-windows"></a>Kontrolowanie okienka zadań w wielu oknach
 Niestandardowe okienka zadań są skojarzone z oknem ramki dokumentu, które przedstawia użytkownikowi widok dokumentu lub elementu. Okienko zadań jest widoczne tylko wtedy, gdy skojarzone okno jest widoczne.

 Aby określić, które okno wyświetla niestandardowe okienko zadań, użyj odpowiedniego przeciążenia metody <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> podczas tworzenia okienka zadań:

- Aby skojarzyć okienko zadań z aktywnym oknem, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody .

- Aby skojarzyć okienko zadań z dokumentem hostowany w określonym oknie, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody .

  Niektóre aplikacje pakietu Office wymagają jawnych instrukcji dotyczących tego, kiedy utworzyć lub wyświetlić okienko zadań, gdy jest otwarte więcej niż jedno okno. Dlatego należy rozważyć miejsce wystąpienia niestandardowego okienka zadań w kodzie, aby upewnić się, że okienko zadań jest wyświetlane z odpowiednimi dokumentami lub elementami w aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie niestandardowymi okienkami zadań w oknach aplikacji.](#Managing)

## <a name="access-the-application-from-the-task-pane"></a>Uzyskiwanie dostępu do aplikacji z okienka zadań
 Jeśli chcesz zautomatyzować aplikację z kontrolki użytkownika, możesz bezpośrednio uzyskać dostęp do modelu obiektów przy użyciu `Globals.ThisAddIn.Application` w kodzie. Klasa `Globals` statyczna zapewnia dostęp do `ThisAddIn` obiektu . Pole `Application` tego obiektu jest punktem wejścia do modelu obiektów aplikacji.

 Aby uzyskać więcej informacji `Application` na temat pola `ThisAddIn` obiektu, zobacz Program [VSTO Add-ins ( Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)). Aby uzyskać przewodnik, który pokazuje, jak zautomatyzować aplikację z niestandardowego okienka zadań, zobacz Walkthrough: Automatic an application from a custom task pane (Przewodnik: automatyczne stosowanie aplikacji [z niestandardowego okienka zadań).](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) Aby uzyskać więcej informacji na temat `Globals` klasy , zobacz Globalny dostęp do obiektów w [projektach pakietu Office.](../vsto/global-access-to-objects-in-office-projects.md)

## <a name="manage-the-user-interface-of-the-task-pane"></a>Zarządzanie interfejsem użytkownika okienka zadań
 Po utworzeniu okienka zadań można użyć właściwości i zdarzeń obiektu do sterowania interfejsem użytkownika okienka zadań i reagowania na zmiany w <xref:Microsoft.Office.Tools.CustomTaskPane> okienku zadań przez użytkownika.

### <a name="make-the-custom-task-pane-visible"></a>Ujmij niestandardowe okienko zadań jako widoczne
 Domyślnie okienko zadań nie jest widoczne. Aby okienko zadań było widoczne, należy ustawić właściwość <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> na **wartość true.**

 Użytkownicy mogą zamknąć okienko zadań w  dowolnym momencie, klikając przycisk Zamknij (X) w rogu okienka zadań. Nie ma jednak domyślnego sposobu, aby użytkownicy ponownie otwierali niestandardowe okienko zadań. Jeśli użytkownik zamknie niestandardowe okienko zadań, nie będzie mógł ponownie wyświetlić niestandardowego okienka zadań, chyba że udostępnisz sposób jego wyświetlania.

 W przypadku tworzenia niestandardowego okienka zadań w dodatku narzędzi VSTO należy również utworzyć element interfejsu użytkownika, taki jak przycisk, który użytkownicy mogą kliknąć, aby wyświetlić lub ukryć niestandardowe okienko zadań. Jeśli tworzysz niestandardowe okienko zadań w aplikacji Microsoft Office obsługującej dostosowywanie wstążki, możesz dodać grupę kontrolek do wstążki za pomocą przycisku, który wyświetla lub ukrywa niestandardowe okienko zadań. Aby uzyskać przewodnik, który pokazuje, jak to zrobić, zobacz [Przewodnik: synchronizowanie](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)niestandardowego okienka zadań za pomocą przycisku wstążki .

 Jeśli tworzysz niestandardowe okienko zadań w aplikacji Microsoft Office, która nie obsługuje dostosowywania wstążki, możesz dodać okienko, które wyświetla lub ukrywa <xref:Microsoft.Office.Core.CommandBarButton> niestandardowe okienko zadań.

### <a name="modify-the-appearance-of-the-task-pane"></a>Modyfikowanie wyglądu okienka zadań
 Rozmiar i lokalizację niestandardowego okienka zadań można kontrolować przy użyciu właściwości <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu. Wiele innych zmian wyglądu niestandardowego okienka zadań można wprowadzić przy użyciu właściwości obiektu zawartego w <xref:System.Windows.Forms.UserControl> niestandardowym okienku zadań. Na przykład można określić obraz tła dla niestandardowego okienka zadań przy użyciu <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości kontrolki użytkownika.

 W poniższej tabeli wymieniono zmiany, które można wprowadzić w niestandardowym okienku zadań przy użyciu <xref:Microsoft.Office.Tools.CustomTaskPane> właściwości.

|Zadanie|Właściwość|
|----------|--------------|
|Aby zmienić rozmiar okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|
|Aby zmienić lokalizację okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|
|Aby ukryć okienko zadań lub sprawić, aby było widoczne|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|
|Aby uniemożliwić użytkownikowi zmianę lokalizacji okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|

### <a name="program-custom-task-pane-events"></a>Zdarzenia niestandardowego okienka zadań programu
 Możesz chcieć, aby dodatek narzędzi VSTO odpowiadał, gdy użytkownik zmodyfikuje niestandardowe okienko zadań. Jeśli na przykład użytkownik zmieni orientację okienka z pionowej na poziomą, można zmienić położenie kontrolek.

 W poniższej tabeli wymieniono zdarzenia, które można obsługiwać w celu reagowania na zmiany wprowadzone przez użytkownika w niestandardowym okienku zadań.

|Zadanie|Zdarzenie|
|----------|-----------|
|Odpowiadanie, gdy użytkownik zmienia lokalizację okienka zadań.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|Aby odpowiedzieć, gdy użytkownik ukrywa okienko zadań lub sprawia, że jest widoczne.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>Oczyszczanie zasobów używanych przez okienko zadań
 Po utworzeniu niestandardowego okienka zadań obiekt pozostaje w pamięci tak długo, jak długo <xref:Microsoft.Office.Tools.CustomTaskPane> jest uruchomiony dodatek narzędzi VSTO. Obiekt pozostaje w pamięci nawet wtedy, gdy użytkownik kliknie przycisk **Zamknij** (X) w rogu okienka zadań.

 Aby wyczyścić zasoby używane przez okienko zadań, gdy dodatek narzędzi VSTO jest nadal uruchomiony, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> metody <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> lub . Te metody <xref:Microsoft.Office.Tools.CustomTaskPane> usuwają określony obiekt z `CustomTaskPanes` kolekcji i wywołują metodę obiektu `Dispose` .

 Automatycznie czyści zasoby używane przez niestandardowe okienko zadań, gdy dodatek [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] narzędzi VSTO jest zwalniany. Nie należy wywołać <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> metod lub <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> w `ThisAddIn_Shutdown` programie obsługi zdarzeń w projekcie. Te metody zwęzają obiekt , ponieważ metoda czyści zasoby <xref:System.ObjectDisposedException> używane przez obiekt przed [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.CustomTaskPane> `ThisAddIn_Shutdown` wywołaniu . Aby uzyskać więcej informacji na temat `ThisAddIn_Shutdown` usługi , zobacz Zdarzenia w [projektach pakietu Office.](../vsto/events-in-office-projects.md)

## <a name="manage-custom-task-panes-in-multiple-application-windows"></a><a name="Managing"></a> Zarządzanie niestandardowymi okienkami zadań w wielu oknach aplikacji
 Podczas tworzenia niestandardowego okienka zadań w aplikacji, która używa wielu okien do wyświetlania dokumentów i innych elementów, należy wykonać dodatkowe czynności, aby upewnić się, że okienko zadań jest widoczne, gdy użytkownik tego oczekuje.

 Niestandardowe okienka zadań we wszystkich aplikacjach są skojarzone z oknem ramki dokumentu, które przedstawia użytkownikowi widok dokumentu lub elementu. Okienko zadań jest widoczne tylko wtedy, gdy skojarzone okno jest widoczne. Jednak nie wszystkie aplikacje używają okien ramowych dokumentu w taki sam sposób.

 Następujące grupy aplikacji mają różne wymagania programowe:

- [Outlook](#Outlook)

- [Word, InfoPath i PowerPoint](#WordAndInfoPath)

## <a name="outlook"></a><a name="Outlook"></a> Programu outlook
 Podczas tworzenia niestandardowego okienka zadań dla programu Outlook niestandardowe okienko zadań jest kojarzone z określonym oknem Eksploratora lub Inspektora. Eksploratory to okna, w których wyświetlana jest zawartość folderu, a inspektorzy to okna, które wyświetlają element, taki jak wiadomość e-mail lub zadanie.

 Jeśli chcesz wyświetlić niestandardowe okienko zadań z wieloma oknami Eksplorator lub Inspektor, musisz utworzyć nowe wystąpienie niestandardowego okienka zadań, gdy zostanie otwarte okno Eksplorator lub Inspektor. W tym celu należy obsłużyć zdarzenie, które jest wywoływane podczas tworzenia okna Eksplorator lub Inspektor, a następnie utworzyć okienko zadań w programie obsługi zdarzeń. Można również obsługiwać zdarzenia Eksplorator i Inspektor, aby ukrywać lub wyświetlać okienka zadań w zależności od tego, które okno jest widoczne.

 Aby skojarzyć okienko zadań z określonym Eksploratorem lub Inspektorem, użyj metody w celu utworzenia okienka zadań i przekaż obiekt <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> <xref:Microsoft.Office.Interop.Outlook.Explorer> lub do <xref:Microsoft.Office.Interop.Outlook.Inspector> *parametru okna.* Aby uzyskać więcej informacji na temat tworzenia niestandardowych okienek zadań, zobacz [Omówienie niestandardowych okienek zadań.](../vsto/custom-task-panes.md)

- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>

  Aby monitorować stan okien inspektora, można obsługiwać następujące zdarzenia związane z inspektorem:

- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Zapobieganie wielu wystąpieniom niestandardowego okienka zadań w programie Outlook
 Aby uniemożliwić oknom programu Outlook wyświetlanie wielu wystąpień niestandardowego okienka zadań, należy jawnie usunąć niestandardowe okienko zadań z kolekcji klasy po `CustomTaskPanes` `ThisAddIn` zamknięciu każdego okna. Wywołaj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> metodę w zdarzeniu, które jest wywoływane po zamknięciu okna, takiego jak <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> lub <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close> .

 Jeśli nie usuniesz jawnie niestandardowego okienka zadań, w oknach programu Outlook może być wyświetlanych wiele wystąpień niestandardowego okienka zadań. Program Outlook czasami odtwarza okna, a odzyskane okna zachowują odwołania do wszelkich niestandardowych okienek zadań, które zostały do nich dołączone.

## <a name="word-infopath-and-powerpoint"></a><a name="WordAndInfoPath"></a> Word, InfoPath i PowerPoint
 W programach Word, InfoPath i PowerPoint każdy dokument jest wyświetlany w innym oknie ramki dokumentu. Podczas tworzenia niestandardowego okienka zadań dla tych aplikacji niestandardowe okienko zadań jest skojarzone tylko z określonym dokumentem. Jeśli użytkownik otworzy inny dokument, niestandardowe okienko zadań będzie ukryte, dopóki wcześniejsza wersja dokumentu nie zostanie ponownie widoczna.

 Jeśli chcesz wyświetlić niestandardowe okienko zadań z wieloma dokumentami, utwórz nowe wystąpienie niestandardowego okienka zadań, gdy użytkownik utworzy nowy dokument lub otworzy istniejący dokument. W tym celu należy obsłużyć zdarzenia wywoływane podczas tworzenia lub otwarcia dokumentu, a następnie utworzyć okienko zadań w programach obsługi zdarzeń. Zdarzenia dokumentów można również obsługiwać w celu ukrywania lub wyświetlania okienek zadań w zależności od tego, który dokument jest widoczny.

 Aby skojarzyć okienko zadań z określonym oknem dokumentu, użyj metody do utworzenia okienka zadań i przekaż (dla programu <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> <xref:Microsoft.Office.Interop.Word.Window> Word), (dla programu <xref:Microsoft.Office.Interop.InfoPath.WindowObject> InfoPath) lub [DocumentWindow](/previous-versions/office/developer/office-2010/ff762047(v=office.14)) (dla programu PowerPoint) do parametru *okna.*

### <a name="word-events"></a>Zdarzenia programu Word
 Aby monitorować stan okien dokumentów w programie Word, można obsługiwać następujące zdarzenia:

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>

### <a name="infopath-events"></a>Zdarzenia InfoPath
 Aby monitorować stan okien dokumentów w programie InfoPath, można obsługiwać następujące zdarzenia:

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>

### <a name="powerpoint-events"></a>Zdarzenia programu PowerPoint
 Aby monitorować stan okien dokumentów w programie PowerPoint, można obsługiwać następujące zdarzenia:

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOtwórz](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOtwórz](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>Zobacz też
- [How to: Add a custom task pane to an application (Jak dodać niestandardowe okienko zadań do aplikacji)](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Przewodnik: synchronizowanie niestandardowego okienka zadań za pomocą przycisku wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Przewodnik: wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
