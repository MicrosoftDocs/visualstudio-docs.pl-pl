---
title: Niestandardowe okienka zadań
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 205b4739d152186415a811b934a210d5f9a38ac4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615406"
---
# <a name="custom-task-panes"></a>Niestandardowe okienka zadań
  Panele interfejsu użytkownika, które zwykle są zadokowane po jednej stronie okna aplikacji Microsoft Office są okienka zadań. Niestandardowe okienka zadań zapewniają możliwość tworzenia własnych okienka zadań i użytkownikom znany interfejs dostęp do funkcji tego rozwiązania. Na przykład interfejs może zawierać mechanizmy uruchamianie kodu na modyfikowanie dokumentów lub wyświetlania danych ze źródła danych.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
>  Niestandardowego okienka zadań różni się w okienku Akcje. W okienku Akcje stanowi część dostosowań poziomu dokumentu dla programu Microsoft Office Word i Microsoft Office Excel. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).

## <a name="benefits-of-custom-task-panes"></a>Zalety niestandardowych okienek zadań
 Niestandardowe okienka zadań umożliwiają integrowanie funkcji interfejsu użytkownika z dobrze znanych. Możesz szybko tworzyć niestandardowego okienka zadań, za pomocą narzędzi Visual Studio.

### <a name="familiar-user-interface"></a>Interfejs użytkownika z dobrze znanych
 Użytkownicy aplikacji w systemie Microsoft Office są już zaznajomieni z używaniem okienka zadań, takich jak **style i formatowanie** okienka zadań w programie Word. Niestandardowe okienka zadań zachowują się podobnie jak inne okienka zadań w systemie Microsoft Office. Użytkownikom można zadokować niestandardowych okienek zadań na różnych stronach w oknie aplikacji lub ich przeciągnij niestandardowych okienek zadań w dowolnej lokalizacji w oknie. Tworzenia dodatku narzędzi VSTO, który wyświetla wiele niestandardowych okienek zadań w tym samym czasie, a użytkownicy mogą kontrolować osobno każdy okienka zadań.

### <a name="windows-forms-support"></a>Obsługa formularzy Windows
 Interfejs użytkownika niestandardowego okienka zadań utworzoną za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio jest oparta na kontrolek formularzy Windows Forms. Dobrze znanych Windows Forms Designer umożliwia projektowanie interfejsu użytkownika dla niestandardowego okienka zadań. Umożliwia także obsługę powiązań danych w formularzach Windows Forms można powiązać źródła danych z kontrolkami w okienku zadań.

## <a name="create-a-custom-task-pane"></a>Tworzenie niestandardowego okienka zadań
 Możesz utworzyć podstawowe niestandardowego okienka zadań w dwóch etapach:

1. Tworzenie interfejsu użytkownika dla niestandardowego okienka zadań, dodając formanty Windows Forms do <xref:System.Windows.Forms.UserControl> obiektu.

2. Przekazując formantu użytkownika, aby utworzyć wystąpienia niestandardowego okienka zadań <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> obiektu w dodatku VSTO. Ta kolekcja zwraca nowy <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt, który służy do modyfikowania wyglądu okienka zadań i reagowania na zdarzenia użytkownika.

   Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika
 Wszystkie niestandardowe okienka zadań, które są tworzone za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio zawiera <xref:System.Windows.Forms.UserControl> obiektu. Ten formant użytkownika udostępnia interfejs użytkownika niestandardowego okienka zadań. Można utworzyć kontrolkę użytkownika w czasie projektowania lub w czasie wykonywania. Jeśli utworzysz formant użytkownika w czasie projektowania, można użyć programu Windows Forms Designer do utworzenia interfejsu użytkownika okienka zadań.

### <a name="instantiate-the-custom-task-pane"></a>Utwórz wystąpienie niestandardowego okienka zadań
 Po utworzeniu kontrolki użytkownika, który zawiera interfejs użytkownika niestandardowego okienka zadań, należy utworzyć wystąpienie <xref:Microsoft.Office.Tools.CustomTaskPane>. Aby to zrobić, należy przekazać formant użytkownika do <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> w dodatku narzędzi VSTO dla programów, wywołując jedną z <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody. Ta kolekcja jest przedstawiany jako `CustomTaskPanes` pole `ThisAddIn` klasy. Poniższy przykład kodu jest przeznaczona do uruchamiania z `ThisAddIn` klasy.

 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> Metody zwracają nowe <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu. Ten obiekt jest używany, aby zmienić wygląd okienka zadań i reagowania na zdarzenia użytkownika.

### <a name="control-the-task-pane-in-multiple-windows"></a>Kontrolki okienka zadań w wielu okien
 Niestandardowe okienka zadań są skojarzone z oknem ramki dokument przedstawia widok dokumentu lub elementu do użytkownika. W okienku zadań jest widoczna tylko wtedy, gdy okno skojarzone jest widoczne.

 Aby określić, które okno wyświetla niestandardowego okienka zadań, użyj odpowiedniej <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> przeciążenia metody tworzenia okienka zadań:

- Aby skojarzyć okienka zadań z aktywnym oknem, należy użyć <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody.

- Aby skojarzyć okienka zadań z dokumentu, który jest obsługiwany przez określonego okna, należy użyć <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metody.

  Niektóre aplikacje pakietu Office wymaga jawne instrukcje dotyczące można utworzyć lub wyświetlić swoje okienka zadań, gdy jest otwarte okno więcej niż jeden. Dzięki temu należy rozważyć, gdzie można utworzyć wystąpienia niestandardowego okienka zadań w kodzie, aby zapewnić właściwe dokumenty lub elementy w aplikacji okienka zadań. Aby uzyskać więcej informacji, zobacz [Zarządzanie niestandardowych okienek zadań w aplikacji systemu windows](#Managing).

## <a name="access-the-application-from-the-task-pane"></a>Uzyskaj dostęp do aplikacji z okienka zadań
 Jeśli chcesz zautomatyzować aplikacji z kontrolki użytkownika, możesz bezpośrednio uzyskać dostęp modelu obiektów przy użyciu `Globals.ThisAddIn.Application` w kodzie. Statyczne `Globals` klasy zapewnia dostęp do `ThisAddIn` obiektu. `Application` Pola tego obiektu jest punktem wejścia do modelu obiektu aplikacji.

 Aby uzyskać więcej informacji na temat `Application` pole `ThisAddIn` obiektu, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md). Aby uzyskać wskazówki, który demonstruje sposób automatyzacja aplikacji z niestandardowego okienka zadań, zobacz [instruktażu: Automatyczne aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Aby uzyskać więcej informacji na temat `Globals` klasy, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="manage-the-user-interface-of-the-task-pane"></a>Zarządzanie interfejsem użytkownika okienka zadań
 Po utworzeniu okienka zadań, można użyć właściwości i zdarzenia <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt do kontrolowania interfejsu użytkownika w okienku zadań i odpowiadać, jeśli użytkownik zmieni okienka zadań.

### <a name="make-the-custom-task-pane-visible"></a>Ustawienie widoczności niestandardowego okienka zadań
 Domyślnie okienka zadań nie jest widoczny. Aby wyświetlić okienko zadań, należy ustawić <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> właściwości **true**.

 Użytkownikom można zamknąć okienko zadań w dowolnym momencie, klikając **Zamknij** przycisku (X) w rogu okienka zadań. Jednak nie ma domyślnego możliwości dla użytkowników ponownie otworzyć niestandardowego okienka zadań. Jeśli użytkownik zamknie niestandardowego okienka zadań, ten użytkownik nie można wyświetlić niestandardowego okienka zadań ponownie, jeśli nie podasz sposób, aby go wyświetlić.

 Jeśli utworzysz niestandardowego okienka zadań w dodatku narzędzi VSTO dla programów, należy również utworzyć elementu interfejsu użytkownika, takie jak przycisk, który użytkownicy mogą kliknąć, aby wyświetlić lub ukryć niestandardowego okienka zadań. Jeśli utworzysz niestandardowego okienka zadań w aplikacji pakietu Microsoft Office, który obsługuje dostosowywania Wstążki można dodać grupę formantów na Wstążce za pomocą przycisku, który wyświetla lub ukrywa niestandardowego okienka zadań. Aby uzyskać wskazówki, które pokazuje, jak to zrobić, zobacz [instruktażu: Synchronizuj niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

 Jeśli utworzysz niestandardowego okienka zadań w aplikacji pakietu Microsoft Office, który nie obsługuje dostosowywania wstążki, można dodać <xref:Microsoft.Office.Core.CommandBarButton> , wyświetla lub ukrywa niestandardowego okienka zadań.

### <a name="modify-the-appearance-of-the-task-pane"></a>Modyfikowanie wyglądu okienka zadań
 Można kontrolować rozmiar i położenie niestandardowego okienka zadań, które znajdują się za pomocą właściwości <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu. Możesz wprowadzić wielu inne zmiany wyglądu niestandardowego okienka zadań przy użyciu właściwości <xref:System.Windows.Forms.UserControl> obiekt, który jest zawarty w niestandardowego okienka zadań. Na przykład można określić obraz tła dla niestandardowego okienka zadań przy użyciu <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości kontrolki użytkownika.

 W poniższej tabeli wymieniono zmiany można wprowadzać niestandardowego okienka zadań przy użyciu <xref:Microsoft.Office.Tools.CustomTaskPane> właściwości.

|Zadanie|Właściwość|
|----------|--------------|
|Aby zmienić rozmiar okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|
|Aby zmienić lokalizację okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|
|Aby ukryć okienko zadań lub stał się widoczny|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|
|Aby uniemożliwić użytkownikowi korzystanie ze zmianą lokalizacji okienka zadań|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|

### <a name="program-custom-task-pane-events"></a>Zdarzenia w okienku zadania niestandardowego programu
 Możesz dodatku narzędzi VSTO dla programów odpowiadać, jeśli użytkownik modyfikuje niestandardowego okienka zadań. Na przykład jeśli użytkownik zmieni się orientację okienka z pionowej na poziomą, można zmienić położenie kontrolki.

 W poniższej tabeli wymieniono zdarzenia, które może obsłużyć do reagowania na zmiany wprowadzone przez użytkownika do niestandardowego okienka zadań.

|Zadanie|Zdarzenie|
|----------|-----------|
|Aby odpowiedzieć, gdy użytkownik zmieni się Lokalizacja okienka zadań.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|Aby odpowiedzieć, gdy użytkownik ukrywa okienko zadań lub sprawia, że widoczne.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>Oczyszczanie zasobów używanych przez okienka zadań
 Po utworzeniu niestandardowego okienka zadań, <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu pozostaje w pamięci tak długo, jak dodatku narzędzi VSTO dla programów jest uruchomiona. Obiekt pozostaje w pamięci, nawet w przypadku, po użytkownik klika polecenie **Zamknij** przycisku (X) w rogu okienka zadań.

 Aby wyczyścić zasoby używane przez okienka zadań, gdy dodatku narzędzi VSTO nadal działa, należy użyć <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> lub <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metody. Te metody usuwają określonego <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu z `CustomTaskPanes` kolekcji, dlatego wywołanie <xref:Microsoft.Office.Tools.CustomTaskPane.Dispose%2A> metody obiektu.

 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Automatycznie czyści zasoby wykorzystywane przez niestandardowego okienka zadań, gdy dodatku narzędzi VSTO jest zwalniana. Nie wywołuj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> lub <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> metody `ThisAddIn_Shutdown` program obsługi zdarzeń w projekcie. Te metody zgłosi <xref:System.ObjectDisposedException>, ponieważ [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] czyści zasoby wykorzystywane przez <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt przed `ThisAddIn_Shutdown` jest wywoływana. Aby uzyskać więcej informacji na temat `ThisAddIn_Shutdown`, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)

##  <a name="Managing"></a> Zarządzanie niestandardowych okienek zadań w wiele okien aplikacji
 Podczas tworzenia niestandardowego okienka zadań w aplikacji, która wyświetla dokumenty i inne elementy przy użyciu wielu okien, należy wykonać dodatkowe czynności, aby upewnić się, że w okienku zadań jest widoczna po użytkownik oczekuje.

 Niestandardowe okienka zadań we wszystkich aplikacjach są skojarzone z oknem ramki dokument przedstawia widok dokumentu lub elementu do użytkownika. W okienku zadań jest widoczna tylko wtedy, gdy okno skojarzone jest widoczne. Jednak nie wszystkie aplikacje użyć okien ramowych dokumentu, ten sam sposób.

 Następujące grupy aplikacji nie mają wymagania dotyczące opracowywania inną:

- [Outlook](#Outlook)

- [Word, InfoPath i PowerPoint](#WordAndInfoPath)

  ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Zarządzanie okienka zadań w dodatkach VSTO programu Word? ](http://go.microsoft.com/fwlink/?LinkId=136781).

##  <a name="Outlook"></a> Program Outlook
 Po utworzeniu niestandardowego okienka zadań programu Outlook niestandardowego okienka zadań jest skojarzony z określonym oknie Eksploratora lub Inspektora. Eksploratory usługi są systemu windows, które wyświetlają zawartość folderu i inspektorzy, wyświetlające element, taki jak wiadomość e-mail lub zadania.

 Jeśli chcesz wyświetlić niestandardowego okienka zadań z wielu Eksploratora lub Inspektora systemu windows, musisz utworzyć nowe wystąpienie klasy niestandardowego okienka zadań, po otwarciu okna Eksploratora lub Inspektora. Aby to zrobić, obsługi zdarzenia, które jest wywoływane, gdy stworzono okno Eksploratora lub Inspektora, a następnie utwórz okienka zadań w obsłudze zdarzeń. Może również obsługiwać Explorer i Inspektor zdarzenia, aby ukryć lub wyświetlanie okienka zadań w zależności od tego, w jakim oknie jest widoczna.

 Aby skojarzyć okienka zadań z określonym Eksploratora lub Inspektora, należy użyć <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metodę, aby utworzyć okienka zadań i przekazać <xref:Microsoft.Office.Interop.Outlook.Explorer> lub <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt *okna* parametru. Aby uzyskać więcej informacji na temat tworzenia niestandardowych okienek zadań, zobacz [Omówienie okienka zadań niestandardowe](../vsto/custom-task-panes.md).

- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>

  Aby monitorować stan Inspektor systemu windows, może obsługiwać następujące zdarzenia związane z Inspektor:

- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Zapobieganie wielu wystąpień niestandardowego okienka zadań w programie Outlook
 Aby zapobiec wyświetlania wielu wystąpień niestandardowego okienka zadań systemu windows w programie Outlook, jawnie usunąć niestandardowego okienka zadań z `CustomTaskPanes` zbiór `ThisAddIn` klasy po zamknięciu każdego okna. Wywołaj <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> in zdarzenie, które jest wywoływane, gdy okno zostanie zamknięte, takich jak metoda <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> lub <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>.

 Nie usuwaj jawnie niestandardowego okienka zadań, systemu windows w programie Outlook może zawierać wiele wystąpień niestandardowego okienka zadań. Outlook czasami jest odtwarzana systemu windows i windows odtwarzania zachowywanie odwołania do żadnych niestandardowych okienek zadań, które zostały dołączone do nich.

##  <a name="WordAndInfoPath"></a> Word, InfoPath i PowerPoint
 Word, InfoPath i PowerPoint wyświetlić każdy dokument w oknie ramowym innego dokumentu. Podczas tworzenia niestandardowego okienka zadań w przypadku tych aplikacji niestandardowego okienka zadań jest skojarzony tylko z określonym dokumentem. Jeśli użytkownik otwiera innego dokumentu, niestandardowego okienka zadań jest ukryta, do momentu wyświetlenia dokumentu wcześniej ponownie.

 Jeśli chcesz wyświetlić niestandardowego okienka zadań z wieloma dokumentami, Utwórz nowe wystąpienie klasy niestandardowego okienka zadań, gdy użytkownik tworzy nowy dokument lub otwiera istniejący dokument. Aby to zrobić, obsługi zdarzeń, które są wywoływane, gdy dokument zostanie utworzony lub otwarty, a następnie utwórz okienka zadań w procedurze obsługi zdarzeń. Może również obsługiwać zdarzenia dokumentu, aby ukryć lub wyświetlanie okienka zadań w zależności od tego, który dokument jest widoczna.

 Aby skojarzyć okienka zadań z oknem określonego dokumentu, należy użyć <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> metodę, aby utworzyć okienka zadań i przekazać <xref:Microsoft.Office.Interop.Word.Window> (dla programu Word), <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (dla programu InfoPath), lub <xref:Microsoft.Office.Interop.PowerPoint.DocumentWindow> (dla programu PowerPoint) do *okna*parametru.

### <a name="word-events"></a>Zdarzenia programu Word
 Aby monitorować stan okien dokumentu programu Word, może obsługiwać następujące zdarzenia:

-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>

-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>

-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>

-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>

-   <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>

### <a name="infopath-events"></a>Zdarzenia programu InfoPath
 Aby monitorować stan okien dokumentu w programie InfoPath, może obsługiwać następujące zdarzenia:

-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>

-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>

-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>

-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>

-   <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>

### <a name="powerpoint-events"></a>Zdarzenia programu PowerPoint
 Aby monitorować stan okien dokumentu w programie PowerPoint, może obsługiwać następujące zdarzenia:

-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

-   [Microsoft.Office.Interop.PowerPoint.EApplication_Event.WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Przewodnik: Synchronizuj niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
