---
title: Model obiektu Outlook ― omówienie
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3f937b819628414430104782459da65d350dd69
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597715"
---
# <a name="outlook-object-model-overview"></a>Model obiektu Outlook ― omówienie
  Tworzenie dodatków narzędzi VSTO dla programu Microsoft Office Outlook, możesz korzystać z obiektami, które są dostarczane przez model obiektów programu Outlook. Model obiektu Outlook zawiera klasy i interfejsy, które reprezentują elementy interfejsu użytkownika. Na przykład <xref:Microsoft.Office.Interop.Outlook.Application> obiekt reprezentuje całej aplikacji, <xref:Microsoft.Office.Interop.Outlook.Folder> obiekt reprezentuje folder, który zawiera wiadomości e-mail lub innych elementów i <xref:Microsoft.Office.Interop.Outlook.MailItem> obiekt reprezentuje wiadomości e-mail.

 Ten temat zawiera krótkie omówienie niektórych obiektów głównych w modelu obiektów programu Outlook. Zasoby można znaleźć więcej informacji na temat cały model obiektu Outlook, można zobaczyć [zapoznaj się z dokumentacją model obiektu Outlook](#refdoc).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Tworzenie raportu niestandardowego zadania za pomocą programu Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130315).

## <a name="access-objects-in-an-outlook-project"></a>Uzyskiwanie dostępu do obiektów w projekcie programu Outlook
 Wiele obiektów, z którymi możesz wchodzić w interakcje w programie Outlook. Aby skutecznie użyć modelu obiektów, należy zapoznać się z następujących obiektów najwyższego poziomu:

-   <xref:Microsoft.Office.Interop.Outlook.Application>

-   <xref:Microsoft.Office.Interop.Outlook.Explorer>

-   <xref:Microsoft.Office.Interop.Outlook.Inspector>

-   <xref:Microsoft.Office.Interop.Outlook.Folder>

-   <xref:Microsoft.Office.Interop.Outlook.MailItem>

-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>

-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>Obiekt aplikacji
 <xref:Microsoft.Office.Interop.Outlook.Application> Obiekt reprezentuje aplikacji Outlook i jest obiektem najwyższego poziomu w modelu obiektów programu Outlook. Najważniejsze elementy członkowskie tego obiektu należą:

- [Createitem —](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) metodę, która służy do tworzenia nowych elementów takich jak wiadomości e-mail, zadania lub terminu.

- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> Właściwość, która umożliwia dostęp do systemu windows, które wyświetlają zawartość folderu w interfejsie użytkownika (UI) programu Outlook.

- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> Właściwość, która umożliwia dostęp do systemu windows, które wyświetlają zawartość pojedynczy element, takich jak wiadomości e-mail wiadomości lub żądania spotkania.

  Aby pobrać wystąpienie obiektu <xref:Microsoft.Office.Interop.Outlook.Application> obiektu, należy użyć aplikacji zakresie `ThisAddIn` klasy w projekcie. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

> [!NOTE]
>  Aby uniknąć wyświetlania ostrzeżenia o zabezpieczeniach podczas korzystania z właściwości i metod, które są blokowane przez strażnik modelu obiektów programu Outlook, uzyskiwanie obiektów programu Outlook w polu aplikacji `ThisAddIn` klasy. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md).

### <a name="explorer-object"></a>Eksplorator obiektów
 <xref:Microsoft.Office.Interop.Outlook.Explorer> Obiekt reprezentuje okno które wyświetla zawartość folderu, który zawiera elementy, takie jak wiadomości e-mail, zadania lub terminy. <xref:Microsoft.Office.Interop.Outlook.Explorer> Obiekt zawiera metody i właściwości, które służy do modyfikowania okna i zdarzenia, które są wywoływane, gdy zmieni się okna.

 Aby uzyskać <xref:Microsoft.Office.Interop.Outlook.Explorer> obiektu, wykonaj jedną z następujących czynności:

-   Użyj <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> właściwość <xref:Microsoft.Office.Interop.Outlook.Application> obiekt, aby uzyskiwać dostęp do wszystkich <xref:Microsoft.Office.Interop.Outlook.Explorer> obiektów w programie Outlook.

-   Użyj <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> metody <xref:Microsoft.Office.Interop.Outlook.Application> można uzyskać <xref:Microsoft.Office.Interop.Outlook.Explorer> czy aktualnie ma fokus.

-   Użyj `GetExplorer` metody <xref:Microsoft.Office.Interop.Outlook.Folder> można uzyskać <xref:Microsoft.Office.Interop.Outlook.Explorer> dla bieżącego folderu.

### <a name="inspector-object"></a>Inspektor obiektu
 <xref:Microsoft.Office.Interop.Outlook.Inspector> Obiekt reprezentuje okno które wyświetla pojedynczy element, takich jak wiadomości e-mail, zadania lub terminu. <xref:Microsoft.Office.Interop.Outlook.Inspector> Obiekt zawiera metody i właściwości, które służy do modyfikowania okna i zdarzenia, które są wywoływane, gdy zmieni się okna.

 Aby uzyskać <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu, wykonaj jedną z następujących czynności:

-   Użyj <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> właściwość <xref:Microsoft.Office.Interop.Outlook.Application> obiekt, aby uzyskiwać dostęp do wszystkich <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektów w programie Outlook.

-   Użyj <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> metody <xref:Microsoft.Office.Interop.Outlook.Application> można uzyskać <xref:Microsoft.Office.Interop.Outlook.Inspector> czy aktualnie ma fokus.

-   Użyj `GetInspector` metoda określonego elementu, takie jak <xref:Microsoft.Office.Interop.Outlook.MailItem> lub <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, aby pobrać narzędzie Inspector, który jest skojarzony z nim.

### <a name="folder-object"></a>Folder obiektu
 <xref:Microsoft.Office.Interop.Outlook.Folder> Obiekt reprezentuje folder, który zawiera wiadomości e-mail, kontakty, zadania i inne elementy. W programie Outlook 16 domyślne <xref:Microsoft.Office.Interop.Outlook.Folder> obiektów.

 Wartość domyślna <xref:Microsoft.Office.Interop.Outlook.Folder> obiekty są zdefiniowane przez <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> wartości wyliczenia. Na przykład

 Odpowiada Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox **skrzynki odbiorczej** folderu w programie Outlook.

 Aby uzyskać przykład pokazujący sposób dostępu do domyślnego <xref:Microsoft.Office.Interop.Outlook.Folder> i Utwórz nowy <xref:Microsoft.Office.Interop.Outlook.Folder>, zobacz [jak: Programowe tworzenie niestandardowych elementów folderu](../vsto/how-to-programmatically-create-custom-folder-items.md).

### <a name="mailitem-object"></a>Obiekt MailItem
 <xref:Microsoft.Office.Interop.Outlook.MailItem> Obiekt reprezentuje wiadomości e-mail. <xref:Microsoft.Office.Interop.Outlook.MailItem> obiekty są zazwyczaj w folderach, takich jak **skrzynki odbiorczej**, **wysłane elementy**, i **Skrzynka nadawcza**. <xref:Microsoft.Office.Interop.Outlook.MailItem> Udostępnia właściwości i metod, które mogą służyć do tworzenia i wysyłania wiadomości e-mail.

 Na przykład, który pokazuje, jak utworzyć wiadomość e-mail, zobacz [jak: Programowe tworzenie elementu poczty e-mail](../vsto/how-to-programmatically-create-an-e-mail-item.md).

### <a name="appointmentitem-object"></a>Obiekt AppointmentItem
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> Obiekt reprezentuje spotkanie, jednorazowe spotkania, lub terminów cyklicznych lub spotkania w **kalendarza** folderu. <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> Obiekt zawiera metody, które wykonują akcje, takie jak odpowiedzi na lub przekazywania wezwania na spotkanie i właściwości, które określają szczegóły spotkania, takie jak miejsce i czas.

 Na przykład, który pokazuje, jak utworzyć termin, zobacz [jak: Programowe tworzenie wezwania na spotkanie](../vsto/how-to-programmatically-create-a-meeting-request.md).

### <a name="taskitem-object"></a>Obiekt TaskItem
 <xref:Microsoft.Office.Interop.Outlook.TaskItem> Obiekt reprezentuje zadanie do wykonania w określonym przedziale czasu. <xref:Microsoft.Office.Interop.Outlook.TaskItem> obiekty znajdują się w **zadania** folderu.

 Aby utworzyć zadanie, należy użyć [createitem —](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) metody <xref:Microsoft.Office.Interop.Outlook.Application> obiektu i przekaż wartość <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> dla parametru.

### <a name="contactitem-object"></a>Obiekt ContactItem
 <xref:Microsoft.Office.Interop.Outlook.ContactItem>Obiekt reprezentuje kontakt w **kontakty** folderu. <xref:Microsoft.Office.Interop.Outlook.ContactItem> obiekty zawierają różne informacje kontaktowe dla osób, które przedstawiają, takie jak adresy, adresy e-mail i numery telefonów.

 Na przykład, który pokazuje, jak utworzyć nowy kontakt, zobacz [jak: Programowe Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Na przykład, który pokazuje, jak do wyszukania istniejącego, zobacz [jak: Programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md).

##  <a name="refdoc"></a> Zapoznaj się z dokumentacją model obiektu Outlook
 Aby uzyskać pełne informacje na temat modelu obiektów programu Outlook mogą odwoływać się do programu Outlook odwołanie do zestawu podstawowej usługi międzyoperacyjnej (PIA) i dokumentacja modelu obiektów języka VBA.

### <a name="primary-interop-assembly-reference"></a>Odwołanie do zestawu podstawowej usługi międzyoperacyjnej
 Odwołania Outlook PIA dokumenty typów na podstawowe zestawy międzyoperacyjne dla programu Outlook 2010. Aby uzyskać więcej informacji, zobacz [odwołanie do zestawu podstawowej usługi międzyoperacyjnej Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).

 Oprócz informacji dla wszystkich typów w zestawów PIA, ta dokumentacja zawiera dodatkowe informacje na temat struktury zestawów PIA i przykłady kodu dla typowych zadań automatyzacji programu Outlook.

### <a name="vba-object-model-reference"></a>Dokumentacja modelu obiektów VBA
 Dokumentacja modelu obiektów VBA dokumenty modelu obiektów programu Outlook, ponieważ jest narażony na język Visual Basic for Applications (VBA) kod. Aby uzyskać więcej informacji, zobacz [dokumentacja modelu obiektów programu Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).

 Wszystkie obiekty i elementy członkowskie w dokumentacja modelu obiektów VBA odnoszą się do typów i członków w PIA programu Outlook. Na przykład obiekt Inspektor dokumentacja modelu obiektów VBA odpowiada <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu w PIA programu Outlook. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy translacji kodu VBA w ramach tego odwołania do kodu języka Visual Basic lub Visual C#, jeśli chcesz korzystać z nich w projekcie dodatku narzędzi VSTO dla programów Outlook utworzonego za pomocą Program Visual Studio.

### <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z elementami kontaktów](../vsto/working-with-contact-items.md)|Zawiera tematy, które pokazują, jak wykonywać zadania przy użyciu kontaktów.|
|[Praca z elementami poczty](../vsto/working-with-mail-items.md)|Zawiera tematy, które pokazują, jak wykonywać zadania związane z elementami poczty.|
|[Praca z folderami](../vsto/working-with-folders.md)|Zawiera tematy, które pokazują, jak wykonywać zadania przy użyciu folderów.|
|[Praca z elementami kalendarza](../vsto/working-with-calendar-items.md)|Zawiera tematy, które pokazują, jak wykonać zadania z elementami kalendarza.|
|[Instrukcje: Programowe wyznaczanie bieżącego elementu programu Outlook](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Pokazuje sposób wyświetlania nazwy bieżącego folderu i niektóre informacje na temat wybranego elementu.|
