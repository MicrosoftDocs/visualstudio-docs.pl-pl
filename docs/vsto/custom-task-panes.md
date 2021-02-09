---
title: Niestandardowe okienka zadań
description: Dowiedz się, że niestandardowe okienka zadań umożliwiają utworzenie własnego okienka zadań i udostępnienie użytkownikom znanego interfejsu umożliwiającego dostęp do funkcji rozwiązania.
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
ms.openlocfilehash: 8ed86cb10f6521e5863562cdb67e768b1a2367d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850038"
---
# <a name="custom-task-panes"></a>Niestandardowe okienka zadań
  Okienka zadań to panele interfejsu użytkownika, które zwykle są zadokowane po jednej stronie okna w aplikacji Microsoft Office. Niestandardowe okienka zadań umożliwiają utworzenie własnego okienka zadań i udostępnienie użytkownikom znanego interfejsu umożliwiającego dostęp do funkcji rozwiązania. Na przykład interfejs może zawierać kontrolki, które uruchamiają kod, aby modyfikować dokumenty lub wyświetlać dane ze źródła danych.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Niestandardowe okienko zadań różni się od okienka Akcje. Okienko akcje jest częścią dostosowania na poziomie dokumentu dla programów Microsoft Office Word i Microsoft Office Excel. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

## <a name="benefits-of-custom-task-panes"></a>Zalety niestandardowych okienek zadań
 Niestandardowe okienka zadań umożliwiają integrację funkcji w znanym interfejsie użytkownika. Możesz szybko utworzyć niestandardowe okienko zadań przy użyciu narzędzi programu Visual Studio.

### <a name="familiar-user-interface"></a>Znany interfejs użytkownika
 Użytkownicy aplikacji w systemie Microsoft Office są już zaznajomieni z korzystaniem z okienek zadań, takich jak okienka zadań **Style i formatowanie** w programie Word. Niestandardowe okienka zadań zachowują się jak inne okienka zadań w systemie Microsoft Office. Użytkownicy mogą dokować niestandardowe okienka zadań na różnych stronach okna aplikacji lub przeciągać niestandardowe okienka zadań do dowolnej lokalizacji w oknie. Można utworzyć dodatek narzędzi VSTO, który wyświetla wiele niestandardowych okienek zadań w tym samym czasie, a użytkownicy mogą kontrolować poszczególne okienka zadań pojedynczo.

### <a name="windows-forms-support"></a>Obsługa formularzy systemu Windows
 Interfejs użytkownika niestandardowego okienka zadań utworzonego przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio jest oparty na kontrolkach Windows Forms. Możesz użyć znanego Projektant formularzy systemu Windows, aby zaprojektować interfejs użytkownika dla niestandardowego okienka zadań. Możesz również użyć obsługi powiązań danych w Windows Forms, aby powiązać źródło danych z kontrolkami w okienku zadań.

## <a name="create-a-custom-task-pane"></a>Tworzenie niestandardowego okienka zadań
 Możesz utworzyć podstawowe okienko zadań niestandardowych w dwóch krokach:

1. Utwórz interfejs użytkownika dla niestandardowego okienka zadań, dodając formanty Windows Forms do <xref:System.Windows.Forms.UserControl> obiektu.

2. Utwórz wystąpienie niestandardowego okienka zadań, przekazując kontrolkę użytkownika do <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> obiektu w dodatku VSTO. Ta kolekcja zwraca nowy <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt, którego można użyć do zmodyfikowania wyglądu okienka zadań i reagowania na zdarzenia użytkownika.

   Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika
 Wszystkie niestandardowe okienka zadań, które są tworzone przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, zawierają <xref:System.Windows.Forms.UserControl> obiekt. Ta kontrolka użytkownika udostępnia interfejs użytkownika niestandardowego okienka zadań. Kontrolkę użytkownika można utworzyć w czasie projektowania lub w czasie wykonywania. Jeśli utworzysz kontrolkę użytkownika w czasie projektowania, możesz użyć Projektant formularzy systemu Windows, aby skonstruować interfejs użytkownika okienka zadań.

### <a name="instantiate-the-custom-task-pane"></a>Tworzenie wystąpienia niestandardowego okienka zadań
 Po utworzeniu kontrolki użytkownika zawierającej interfejs użytkownika niestandardowego okienka zadań należy utworzyć wystąpienie <xref:Microsoft.Office.Tools.CustomTaskPane> . W tym celu Przekaż kontrolkę użytkownika do funkcji <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> w dodatku VSTO, wywołując jedną z <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metod. Ta kolekcja jest udostępniana jako `CustomTaskPanes` pole `ThisAddIn` klasy. Poniższy przykład kodu jest przeznaczony do uruchomienia z `ThisAddIn` klasy.

 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>Metody zwracają nowy <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt. Za pomocą tego obiektu można modyfikować wygląd okienka zadań i reagować na zdarzenia użytkownika.

### <a name="control-the-task-pane-in-multiple-windows"></a>Kontrolowanie okienka zadań w wielu oknach
 Niestandardowe okienka zadań są skojarzone z oknem ramki dokumentu, które przedstawia widok dokumentu lub elementu użytkownikowi. Okienko zadań jest widoczne tylko wtedy, gdy skojarzone okno jest widoczne.

 Aby określić, które okno wyświetla niestandardowe okienko zadań, użyj odpowiedniego <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> przeciążenia metody podczas tworzenia okienka zadań:

- Aby skojarzyć okienko zadań z aktywnym oknem, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody.

- Aby skojarzyć okienko zadań z dokumentem hostowanym przez określone okno, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody.

  Niektóre aplikacje pakietu Office wymagają jawnych instrukcji podczas tworzenia lub wyświetlania okienka zadań, gdy jest otwarte więcej niż jedno okno. Jest to ważne, aby uwzględnić miejsce, w którym można utworzyć wystąpienie niestandardowego okienka zadań w kodzie, aby upewnić się, że okienko zadań pojawia się z odpowiednimi dokumentami lub elementami w aplikacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie niestandardowymi okienkami zadań w oknach aplikacji](#Managing).

## <a name="access-the-application-from-the-task-pane"></a>Dostęp do aplikacji z okienka zadań
 Jeśli chcesz zautomatyzować aplikację z poziomu kontrolki użytkownika, możesz bezpośrednio uzyskać dostęp do modelu obiektów przy użyciu `Globals.ThisAddIn.Application` kodu. Klasa statyczna `Globals` zapewnia dostęp do `ThisAddIn` obiektu. `Application`Pole tego obiektu jest punktem wejścia do modelu obiektowego aplikacji.

 Aby uzyskać więcej informacji na temat `Application` pola `ThisAddIn` obiektu, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md). Aby zapoznać się z przewodnikiem, który pokazuje, jak zautomatyzować aplikację z niestandardowego okienka zadań, zobacz [Przewodnik: automatyczne działanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Aby uzyskać więcej informacji na temat `Globals` klasy, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="manage-the-user-interface-of-the-task-pane"></a>Zarządzanie interfejsem użytkownika okienka zadań
 Po utworzeniu okienka zadań można użyć właściwości i zdarzeń <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu do sterowania interfejsem użytkownika okienka zadań i odpowiedzi, gdy użytkownik zmieni okienko zadań.

### <a name="make-the-custom-task-pane-visible"></a>Wyświetlanie okienka zadań niestandardowych
 Domyślnie okienko zadań nie jest widoczne. Aby okienko zadań było widoczne, należy ustawić <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> Właściwość na **true**.

 Użytkownicy mogą w dowolnym momencie zamknąć okienko zadań, klikając przycisk **Zamknij** (X) w rogu okienka zadań. Nie ma jednak domyślnego sposobu, aby użytkownicy mogli ponownie otworzyć niestandardowe okienko zadań. Jeśli użytkownik zamknie niestandardowe okienko zadań, ten użytkownik nie będzie mógł ponownie wyświetlić niestandardowego okienka zadań, chyba że zostanie pożądany sposób wyświetlania go.

 W przypadku tworzenia niestandardowego okienka zadań w dodatku VSTO należy również utworzyć element interfejsu użytkownika, taki jak przycisk, który użytkownicy mogą kliknąć, aby wyświetlić lub ukryć niestandardowe okienko zadań. Jeśli utworzysz niestandardowe okienko zadań w aplikacji Microsoft Office, która obsługuje Dostosowywanie wstążki, możesz dodać grupę kontrolek do wstążki z przyciskiem, który wyświetla lub ukrywa niestandardowe okienko zadań. Aby zapoznać się z przewodnikiem, który pokazuje, jak to zrobić, zobacz [Przewodnik: synchronizowanie niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

 Jeśli utworzysz niestandardowe okienko zadań w aplikacji Microsoft Office, która nie obsługuje dostosowywania wstążki, możesz dodać <xref:Microsoft.Office.Core.CommandBarButton> , która wyświetla lub ukrywa niestandardowe okienko zadań.

### <a name="modify-the-appearance-of-the-task-pane"></a>Modyfikowanie wyglądu okienka zadań
 Można kontrolować rozmiar i lokalizację niestandardowego okienka zadań przy użyciu właściwości <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu. Możesz wprowadzić wiele innych zmian wyglądu niestandardowego okienka zadań przy użyciu właściwości <xref:System.Windows.Forms.UserControl> obiektu, który jest zawarty w okienku niestandardowego zadania. Na przykład można określić obraz tła dla niestandardowego okienka zadań przy użyciu <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości kontrolki użytkownika.

 W poniższej tabeli wymieniono zmiany, które można wprowadzić do niestandardowego okienka zadań przy użyciu <xref:Microsoft.Office.Tools.CustomTaskPane> właściwości.

|Zadanie|Właściwość|
|----------|--------------|
|Aby zmienić rozmiar okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|
|Aby zmienić lokalizację okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|
|Aby ukryć okienko zadań lub uczynić je widoczne|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|
|Aby uniemożliwić użytkownikowi zmianę lokalizacji okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|

### <a name="program-custom-task-pane-events"></a>Niestandardowe zdarzenia okienka zadań programu
 Jeśli użytkownik modyfikuje niestandardowe okienko zadań, może być konieczne, aby dodatek VSTO odpowiadał. Na przykład, jeśli użytkownik zmieni orientację okienka z pionowa na pozioma, możesz chcieć zmienić położenie kontrolek.

 Poniższa tabela zawiera listę zdarzeń, które można obsłużyć w celu reagowania na zmiany wprowadzane przez użytkownika do niestandardowego okienka zadań.

|Zadanie|Zdarzenie|
|----------|-----------|
|Reagowanie, gdy użytkownik zmieni lokalizację okienka zadań.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|Reagowanie, gdy użytkownik ukrywa okienko zadań lub wyświetla je.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>Czyszczenie zasobów używanych przez okienko zadań
 Po utworzeniu niestandardowego okienka zadań <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt pozostaje w pamięci, dopóki dodatek VSTO jest uruchomiony. Obiekt pozostaje w pamięci nawet po kliknięciu przycisku **Zamknij** (X) w rogu okienka zadań.

 Aby wyczyścić zasoby używane przez okienko zadań, gdy dodatek VSTO nadal działa, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metod lub. Te metody usuwają określony <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt z `CustomTaskPanes` kolekcji i wywołują `Dispose` metodę obiektu.

 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Automatycznie czyści zasoby używane przez niestandardowe okienko zadań, gdy dodatek narzędzi VSTO zostanie zwolniony. Nie wywołuj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metod lub w programie `ThisAddIn_Shutdown` obsługi zdarzeń w projekcie. Te metody spowodują zgłoszenie elementu <xref:System.ObjectDisposedException> , ponieważ [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] <xref:Microsoft.Office.Tools.CustomTaskPane> przed `ThisAddIn_Shutdown` wywołaniem zostanie wywołane czyszczenie zasobów używanych przez obiekt. Aby uzyskać więcej informacji na temat `ThisAddIn_Shutdown` , zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

## <a name="manage-custom-task-panes-in-multiple-application-windows"></a><a name="Managing"></a> Zarządzanie niestandardowymi okienkami zadań w wielu oknach aplikacji
 W przypadku tworzenia niestandardowego okienka zadań w aplikacji używającej wielu okien do wyświetlania dokumentów i innych elementów należy wykonać dodatkowe czynności, aby upewnić się, że okienko zadań będzie widoczne, gdy użytkownik spodziewa się go.

 Niestandardowe okienka zadań we wszystkich aplikacjach są skojarzone z oknem ramki dokumentu, które przedstawia widok dokumentu lub elementu użytkownikowi. Okienko zadań jest widoczne tylko wtedy, gdy skojarzone okno jest widoczne. Jednak nie wszystkie aplikacje używają okien ramowych dokumentu w taki sam sposób.

 Następujące grupy aplikacji mają różne wymagania programistyczne:

- [Outlook](#Outlook)

- [Word, InfoPath i PowerPoint](#WordAndInfoPath)

## <a name="outlook"></a><a name="Outlook"></a> Programie
 W przypadku tworzenia niestandardowego okienka zadań dla programu Outlook niestandardowe okienko zadań zostanie skojarzone z określonym Eksploratorem lub oknem inspektora. Eksploratory są oknami, które wyświetlają zawartość folderu, a inspektorzy są oknami, które wyświetlają element, taki jak wiadomość e-mail lub zadanie.

 Jeśli chcesz wyświetlić niestandardowe okienko zadań z wieloma oknami Eksploratora lub inspektorem, musisz utworzyć nowe wystąpienie niestandardowego okienka zadań, gdy zostanie otwarte okno Eksploratora lub inspektora. W tym celu należy obsłużyć zdarzenie, które jest zgłaszane podczas tworzenia okna Eksploratora lub Inspektora, a następnie utworzyć okienko zadań w programie obsługi zdarzeń. Możesz także obsłużyć zdarzenia Eksploratora i inspektora, aby ukryć lub wyświetlić okienka zadań w zależności od tego, które okno jest widoczne.

 Aby skojarzyć okienko zadań z określonym Eksploratorem lub inspektorem, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody w celu utworzenia okienka zadań i przekazania <xref:Microsoft.Office.Interop.Outlook.Explorer> <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu lub do parametru *okna* . Aby uzyskać więcej informacji na temat tworzenia niestandardowych okienek zadań, zobacz [niestandardowe okienka zadań — Omówienie](../vsto/custom-task-panes.md).

- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>

  Aby monitorować stan okien inspektorów, można obsłużyć następujące zdarzenia związane z inspektorem:

- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Zapobiegaj wielu wystąpieniem niestandardowego okienka zadań w programie Outlook
 Aby zapobiec wyświetlaniu wielu wystąpień niestandardowego okienka zadań przez program Outlook Windows, należy jawnie usunąć niestandardowe okienko zadań z `CustomTaskPanes` kolekcji `ThisAddIn` klasy po zamknięciu każdego okna. Wywołaj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> metodę w zdarzeniu, które jest zgłaszane, gdy okno zostanie zamknięte, takie jak <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> lub <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close> .

 Jeśli nie usuniesz jawnie okienka zadań niestandardowych, w programie Outlook w systemie Windows może być wyświetlanych wiele wystąpień niestandardowego okienka zadań. Program Outlook czasami odtwarza system Windows, a odtwarzanie odwołuje się do dowolnych niestandardowych okienek zadań, które zostały do nich dołączone.

## <a name="word-infopath-and-powerpoint"></a><a name="WordAndInfoPath"></a> Word, InfoPath i PowerPoint
 Programy Word, InfoPath i PowerPoint wyświetlają każdy dokument w innym oknie ramki dokumentu. Po utworzeniu niestandardowego okienka zadań dla tych aplikacji okienko niestandardowe zadanie jest skojarzone tylko z określonym dokumentem. Jeśli użytkownik otworzy inny dokument, okienko zadania niestandardowego zostanie ukryte, dopóki wcześniejszy dokument nie zostanie ponownie wyświetlony.

 Jeśli chcesz wyświetlić niestandardowe okienko zadań z wieloma dokumentami, Utwórz nowe wystąpienie niestandardowego okienka zadań, gdy użytkownik tworzy nowy dokument lub otwiera istniejący dokument. W tym celu należy obsłużyć zdarzenia, które są wywoływane podczas tworzenia lub otwierania dokumentu, a następnie utworzyć okienko zadań w programach obsługi zdarzeń. Możesz także obsłużyć zdarzenia dokumentu, aby ukryć lub wyświetlić okienka zadań w zależności od tego, który dokument jest widoczny.

 Aby skojarzyć okienko zadań z określonym oknem dokumentu, użyj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody w celu utworzenia okienka zadań i przekazanie (dla programu <xref:Microsoft.Office.Interop.Word.Window> Word),  <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (dla programu InfoPath) lub [DocumentWindow](/previous-versions/office/developer/office-2010/ff762047(v=office.14)) (dla programu PowerPoint) do parametru *okna* .

### <a name="word-events"></a>Zdarzenia programu Word
 Aby monitorować stan okien dokumentu w programie Word, można obsłużyć następujące zdarzenia:

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>

### <a name="infopath-events"></a>Zdarzenia programu InfoPath
 Aby monitorować stan okien dokumentów w programie InfoPath, można obsłużyć następujące zdarzenia:

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>

### <a name="powerpoint-events"></a>Zdarzenia programu PowerPoint
 Aby monitorować stan okien dokumentów w programie PowerPoint, można obsłużyć następujące zdarzenia:

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: Automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Przewodnik: synchronizowanie niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
