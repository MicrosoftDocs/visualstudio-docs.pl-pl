---
title: Model obiektów programu Outlook — Omówienie
description: Dowiedz się, w jaki sposób można korzystać z obiektów dostarczanych przez model obiektów programu Outlook w celu opracowania dodatków narzędzi VSTO dla programu Microsoft Outlook.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 316ead76be1f84fccc6f675b204587008e8a194a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885303"
---
# <a name="outlook-object-model-overview"></a>Model obiektów programu Outlook — Omówienie
  Aby opracowywać dodatki narzędzi VSTO dla Microsoft Office Outlook, można korzystać z obiektów dostarczanych przez model obiektów programu Outlook. Model obiektów programu Outlook zawiera klasy i interfejsy, które reprezentują elementy w interfejsie użytkownika. Na przykład <xref:Microsoft.Office.Interop.Outlook.Application> obiekt reprezentuje całą aplikację, <xref:Microsoft.Office.Interop.Outlook.Folder> obiekt reprezentuje folder zawierający wiadomości e-mail lub inne elementy, a <xref:Microsoft.Office.Interop.Outlook.MailItem> obiekt reprezentuje wiadomość e-mail.

 Ten temat zawiera krótkie omówienie niektórych głównych obiektów w modelu obiektów programu Outlook. Aby uzyskać więcej informacji o zasobach, które można dowiedzieć się więcej na temat całego modelu obiektów programu Outlook, zobacz [Korzystanie z dokumentacji modelu obiektów programu Outlook](#refdoc).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-objects-in-an-outlook-project"></a>Dostęp do obiektów w projekcie programu Outlook
 Program Outlook udostępnia wiele obiektów, z którymi można korzystać. Aby efektywnie korzystać z modelu obiektów, należy zapoznać się z następującymi obiektami najwyższego poziomu:

- <xref:Microsoft.Office.Interop.Outlook.Application>

- <xref:Microsoft.Office.Interop.Outlook.Explorer>

- <xref:Microsoft.Office.Interop.Outlook.Inspector>

- <xref:Microsoft.Office.Interop.Outlook.Folder>

- <xref:Microsoft.Office.Interop.Outlook.MailItem>

- <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

- <xref:Microsoft.Office.Interop.Outlook.TaskItem>

- <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>Obiekt aplikacji
 <xref:Microsoft.Office.Interop.Outlook.Application>Obiekt reprezentuje aplikację Outlook i jest obiektem najwyższego poziomu w modelu obiektów programu Outlook. Niektóre z najważniejszych elementów członkowskich tego obiektu obejmują:

- Metoda tworzenia [elementu](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) , której można użyć do utworzenia nowego elementu, takiego jak wiadomość e-mail, zadanie lub termin.

- <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A>Właściwość, której można użyć w celu uzyskania dostępu do okna, w którym jest wyświetlana zawartość folderu w interfejsie użytkownika programu Outlook.

- <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A>Właściwość, której można użyć w celu uzyskania dostępu do okna, w którym jest wyświetlana zawartość pojedynczego elementu, takiego jak wiadomość e-mail lub prośba o spotkanie.

  Aby uzyskać wystąpienie <xref:Microsoft.Office.Interop.Outlook.Application> obiektu, użyj pola aplikacji `ThisAddIn` klasy w projekcie. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

> [!NOTE]
> Aby uniknąć ostrzeżeń zabezpieczeń w przypadku używania właściwości i metod, które są blokowane przez ochronę modelu obiektów programu Outlook, Pobierz obiekty programu Outlook z pola aplikacji `ThisAddIn` klasy. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md).

### <a name="explorer-object"></a>Obiekt Eksploratora
 <xref:Microsoft.Office.Interop.Outlook.Explorer>Obiekt reprezentuje okno, w którym jest wyświetlana zawartość folderu zawierającego elementy, takie jak wiadomości e-mail, zadania lub terminy. <xref:Microsoft.Office.Interop.Outlook.Explorer>Obiekt zawiera metody i właściwości, których można użyć do zmodyfikowania okna i zdarzenia, które są wywoływane, gdy okno zostanie zmienione.

 Aby uzyskać <xref:Microsoft.Office.Interop.Outlook.Explorer> obiekt, wykonaj jedną z następujących czynności:

- Użyj <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> właściwości <xref:Microsoft.Office.Interop.Outlook.Application> obiektu, aby uzyskać dostęp do wszystkich <xref:Microsoft.Office.Interop.Outlook.Explorer> obiektów w programie Outlook.

- Użyj <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> metody <xref:Microsoft.Office.Interop.Outlook.Application> obiektu, aby uzyskać <xref:Microsoft.Office.Interop.Outlook.Explorer> , że aktualnie ma fokus.

- Użyj `GetExplorer` metody <xref:Microsoft.Office.Interop.Outlook.Folder> obiektu, aby uzyskać dostęp do <xref:Microsoft.Office.Interop.Outlook.Explorer> bieżącego folderu.

### <a name="inspector-object"></a>Obiekt Inspector
 <xref:Microsoft.Office.Interop.Outlook.Inspector>Obiekt reprezentuje okno, które wyświetla pojedynczy element, taki jak wiadomość e-mail, zadanie lub termin. <xref:Microsoft.Office.Interop.Outlook.Inspector>Obiekt zawiera metody i właściwości, których można użyć do zmodyfikowania okna i zdarzenia, które są wywoływane, gdy okno zostanie zmienione.

 Aby uzyskać <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, wykonaj jedną z następujących czynności:

- Użyj <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> właściwości <xref:Microsoft.Office.Interop.Outlook.Application> obiektu, aby uzyskać dostęp do wszystkich <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektów w programie Outlook.

- Użyj <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> metody <xref:Microsoft.Office.Interop.Outlook.Application> obiektu, aby uzyskać <xref:Microsoft.Office.Interop.Outlook.Inspector> , że aktualnie ma fokus.

- Użyj `GetInspector` metody określonego elementu, takiej jak <xref:Microsoft.Office.Interop.Outlook.MailItem> lub <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> , aby pobrać skojarzony z nią Inspektor.

### <a name="folder-object"></a>Obiekt folderu
 <xref:Microsoft.Office.Interop.Outlook.Folder>Obiekt reprezentuje folder zawierający wiadomości e-mail, kontakty, zadania i inne elementy. Program Outlook udostępnia 16 <xref:Microsoft.Office.Interop.Outlook.Folder> obiektów domyślnych.

 Obiekty domyślne <xref:Microsoft.Office.Interop.Outlook.Folder> są definiowane przez <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> wartości wyliczenia. Na przykład

 Microsoft. Office. Interop. Outlook. OlDefaultFolders. olFolderInbox odpowiada folderowi **skrzynki odbiorczej** w programie Outlook.

 Aby zapoznać się z przykładem, który pokazuje, jak uzyskać dostęp do domyślnych <xref:Microsoft.Office.Interop.Outlook.Folder> i utworzyć nowy <xref:Microsoft.Office.Interop.Outlook.Folder> , zobacz [How to: programowe tworzenie niestandardowych elementów folderów](../vsto/how-to-programmatically-create-custom-folder-items.md).

### <a name="mailitem-object"></a>Obiekt MailItem
 <xref:Microsoft.Office.Interop.Outlook.MailItem>Obiekt reprezentuje wiadomość e-mail. <xref:Microsoft.Office.Interop.Outlook.MailItem> obiekty są zwykle w folderach, takich jak **Skrzynka odbiorcza**, **wysłane elementy** i **Skrzynka nadawcza**. <xref:Microsoft.Office.Interop.Outlook.MailItem> Opisuje właściwości i metody, których można użyć do tworzenia i wysyłania wiadomości e-mail.

 Przykład pokazujący sposób tworzenia wiadomości e-mail można znaleźć w temacie [How to: programowe tworzenie elementu poczty e-mail](../vsto/how-to-programmatically-create-an-e-mail-item.md).

### <a name="appointmentitem-object"></a>Obiekt AppointmentItem
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>Obiekt reprezentuje spotkanie, termin jednorazowy lub termin cykliczny lub spotkanie w folderze **Calendar** . <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>Obiekt zawiera metody, które wykonują akcje, takie jak odpowiadanie na żądania spotkań lub przekazywanie do nich, oraz właściwości określające szczegóły spotkania, takie jak lokalizacja i czas.

 Aby zapoznać się z przykładem, który pokazuje, jak utworzyć termin, zobacz [How to: programowe tworzenie żądania spotkania](../vsto/how-to-programmatically-create-a-meeting-request.md).

### <a name="taskitem-object"></a>Obiekt TaskItem
 <xref:Microsoft.Office.Interop.Outlook.TaskItem>Obiekt reprezentuje zadanie, które ma zostać wykonane w określonym przedziale czasu. <xref:Microsoft.Office.Interop.Outlook.TaskItem> obiekty znajdują się w folderze **Tasks** .

 Aby utworzyć zadanie, użyj metody [onitem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) <xref:Microsoft.Office.Interop.Outlook.Application> obiektu i przekaż wartość <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> parametru.

### <a name="contactitem-object"></a>Obiekt ContactItem
 <xref:Microsoft.Office.Interop.Outlook.ContactItem>Obiekt reprezentuje kontakt w folderze **kontaktów** . <xref:Microsoft.Office.Interop.Outlook.ContactItem> obiekty zawierają różne informacje kontaktowe dla osób, które reprezentują, takie jak adresy ulic, adresy e-mail i numery telefonów.

 Aby zapoznać się z przykładem, który pokazuje, jak utworzyć nowy kontakt, zobacz [How to: programowe Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Aby zapoznać się z przykładem, który pokazuje, jak wyszukiwać istniejący kontakt, zobacz [How to: programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md).

## <a name="use-the-outlook-object-model-documentation"></a><a name="refdoc"></a> Korzystanie z dokumentacji modelu obiektów programu Outlook
 Aby uzyskać pełne informacje na temat modelu obiektów programu Outlook, można odwołać się do odwołania do podstawowego zestawu międzyoperacyjnego (PIA) programu Outlook i odwołania do modelu obiektów VBA.

### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoperacyjnego
 Dokumentacja PIA programu Outlook umożliwia dokumentowanie typów w podstawowych zestawach międzyoperacyjnych dla programu Outlook 2010. Aby uzyskać więcej informacji, zobacz [odwołanie do podstawowego zestawu międzyoperacyjnego programu Outlook 2010](/previous-versions/office/developer/office-2010/bb652780(v=office.14)).

 Oprócz przekazywania informacji dla wszystkich typów w zestawów Pia, Ta dokumentacja zawiera również dodatkowe informacje na temat struktury zestawów PIA i kodu przykładów dla typowych zadań automatyzacji programu Outlook.

### <a name="vba-object-model-reference"></a>Odwołanie do modelu obiektów VBA
 Dokumentacja modelu obiektów VBA dokumentuje model obiektów programu Outlook, który jest udostępniany w kodzie Visual Basic for Applications (VBA). Aby uzyskać więcej informacji, zobacz temat informacje o [modelu obiektów w programie Outlook 2010](/office/vba/api/overview/Outlook/object-model).

 Wszystkie obiekty i elementy członkowskie w odniesieniu do modelu obiektów VBA odpowiadają typom i członkom w PIAu programu Outlook. Na przykład obiekt inspektora w odniesieniu do modelu obiektów VBA odnosi się do <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu w Piau programu Outlook. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod języka VBA w tym odwołaniu do Visual Basic lub Visual C#, jeśli chcesz użyć ich w projekcie Add-In VSTO programu Outlook utworzonym przy użyciu programu Visual Studio.

### <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Pracuj z elementami kontaktów](../vsto/working-with-contact-items.md)|Zawiera tematy pokazujące, jak wykonywać zadania z kontaktami.|
|[Pracuj z elementami poczty](../vsto/working-with-mail-items.md)|Zawiera tematy pokazujące, jak wykonywać zadania z elementami poczty.|
|[Pracuj z folderami](../vsto/working-with-folders.md)|Zawiera tematy pokazujące, jak wykonywać zadania z użyciem folderów.|
|[Pracuj z elementami kalendarza](../vsto/working-with-calendar-items.md)|Zawiera tematy pokazujące, jak wykonywać zadania z elementami kalendarza.|
|[Instrukcje: programowe Określanie bieżącego elementu programu Outlook](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Pokazuje, jak wyświetlić nazwę bieżącego folderu oraz informacje o wybranym elemencie.|
