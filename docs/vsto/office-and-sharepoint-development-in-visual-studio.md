---
title: Programowanie Office i programu SharePoint w Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4eb2e58070a4be9d9dd5d70fdaddfd5eee997a41
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607060"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Programowanie Office i programu SharePoint w Visual Studio
  Możesz rozszerzyć Microsoft Office i SharePoint, tworząc uproszczone aplikacji lub dodatku pobierany przez użytkowników z [Store Office](https://store.office.com/) lub organizacji w katalogu lub przez tworzenie rozwiązaniem opartym na programie .NET Framework, którego użytkownik należy zainstalować na komputer.

 W tym temacie:

-   [Tworzenie dodatków dla pakietu Office i programu SharePoint](#Apps)

-   [Tworzenie dodatku narzędzi VSTO](#Add-ins)

-   [Tworzenie rozwiązań programu SharePoint](#Solutions)

##  <a name="Apps"></a> Tworzenie dodatków dla pakietu Office i programu SharePoint
 Pakiet Office 2013 i programu SharePoint 2013 wprowadzono nowy dodatek model, który ułatwia tworzenie, rozpowszechniać i Zarabiaj dodatków rozszerzających pakiet Office i programu SharePoint.  Uruchomić te dodatki pakietu Office lub usługi SharePoint Online, a użytkownicy mogą wchodzić w interakcje z nimi z wielu urządzeń.

 Dowiedz się, jak korzystać z nowych [dodatku pakietu Office modelu](/office/dev/add-ins/overview/office-add-ins) rozszerzenie obsługi pakietu Office dla użytkowników.

 Dodatki te mają udzielaniu małe w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.  Aby rozpocząć pracę, użyj narzędzia Office Developer Tools w programie Visual Studio lub prostego, działającego narzędzia opartego na sieci web kodu pakietu Office 365 rozwoju Napa, która pozwala na tworzenie projektów, pisanie kodu i uruchomić dodatki w przeglądarce sieci.

 ![Aplikacje dla pakietu Office i programu SharePoint modelu koncepcyjnego](../vsto/media/officeandsharepointapps2015.png "aplikacje dla pakietu Office i programu SharePoint model koncepcyjny")

### <a name="build-an-office-add-in"></a>Tworzenie dodatku pakietu Office
 Aby rozszerzyć funkcje pakietu Office, twórz dodatku pakietu Office. Jest zasadniczo stroną internetową, która znajduje się w aplikacji pakietu Office, takich jak Excel, Word, Outlook i PowerPoint. Aplikację można dodać funkcje do dokumentów, arkuszy, wiadomości e-mail, terminy, prezentacje i projektów.

 Możesz sprzedawać swoją aplikację w Store pakietu Office.  [Store Office](https://store.office.com/) ułatwia wprowadzanie do obiegu dodatków, zarządzanie aktualizacjami i śledzenie danych telemetrycznych. Można również publikować aplikację dla użytkowników z katalogu aplikacji w programie SharePoint lub na serwerze Exchange.

 Następujące aplikacja dla pakietu Office zawiera dane arkusza w mapy Bing.

 ![Aplikacja zawartości dla pakietu Office](../vsto/media/appforoffice.png "aplikacji zawartości dla pakietu Office")

 **Dowiedz się więcej**

|Zadanie|Zobacz|
|--------|---------|
|Dowiedz się więcej o dodatki pakietu Office, a następnie utworzyć jeden.|[Dodatki pakietu Office](/office/dev/add-ins/publish/publish)|
|Porównaj różne sposoby, w którym można rozszerzyć pakietu Office i zdecyduj, czy należy używać aplikację lub dodatek pakietu Office.|[Harmonogram działania dla dodatków pakietu Office, VSTO i VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|

### <a name="build-a-sharepoint-add-in"></a>Tworzenie dodatku programu SharePoint
 Aby rozszerzyć programu SharePoint dla użytkowników, tworzenie dodatku programu SharePoint. Jest zasadniczo aplikacją małej, łatwy w użyciu, autonomicznej, która rozwiązuje na potrzeby użytkowników lub firmy.

 Możesz sprzedawać swoje aplikacje dla programu SharePoint w [Store Office](https://store.office.com/). Możesz również opublikować dodatku dla użytkowników z katalogu dodatku w programie SharePoint.  Właściciele witryn można zainstalować, uaktualnianie i odinstalowywanie dodatku w swoich witrynach programu SharePoint bez pomocy serwera farmy lub administratorem zbioru witryn.

 Oto przykład aplikacji programu SharePoint, która ułatwia użytkownikom zarządzanie kontaktów służbowych.

 ![Business menedżera kontaktu aplikacji dla programu SharePoint](../vsto/media/appforsharepoint.png "firmy kontaktu Menedżera aplikacji dla programu SharePoint")

 **Dowiedz się więcej**

|Zadanie|Zobacz|
|--------|---------|
|Dowiedz się więcej o dodatkach programu SharePoint, a następnie utworzyć jeden.|[Dodatki programu SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|Porównaj dodatków programu SharePoint przy użyciu tradycyjnych rozwiązań programu SharePoint.|[Dodatków programu SharePoint w porównaniu z rozwiązaniami SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Wybierz, czy do tworzenia dodatku programu SharePoint lub rozwiązania programu SharePoint.|[Wybór między dodatków programu SharePoint i rozwiązań SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

##  <a name="Add-ins"></a> Tworzenie dodatku narzędzi VSTO
 Utwórz dodatek narzędzi VSTO dla pakietu Office 2007 lub Office 2010 lub Rozszerz pakiet Office 2013 i Office 2016 poza to, co można zrobić za pomocą dodatków pakietu Office. Dodatków narzędzi VSTO uruchomić tylko na pulpicie. Użytkownicy muszą zainstalować dodatków narzędzi VSTO, dzięki czemu są zwykle trudniejsze do wdrożenia i obsługi.  Jednak dodatku narzędzi VSTO dla programów może zostać zintegrowany dokładniej przy użyciu pakietu Office. Na przykład ją dodać karty i kontrolki do wstążki pakietu Office i wykonywanie zaawansowana Automatyzacja zadań, takich jak scalanie dokumentów lub modyfikowania wykresów. Można korzystać z programu .NET Framework i użyć C# i Visual Basic do interakcji z obiektów pakietu Office.

 Oto przykład jakie dodatku narzędzi VSTO zrobić. Ten dodatek narzędzi VSTO dla programów dodaje formanty wstążki, niestandardowego okienka zadań i okno dialogowe do programu PowerPoint.

 ![Rozwiązanie dodatku programu PowerPoint](../vsto/media/powerpointaddin.png "rozwiązanie dodatku programu PowerPoint")

 **Dowiedz się więcej**

|Zadanie|Odczyt|
|--------|----------|
|Porównaj różne sposoby, w którym można rozszerzyć pakietu Office i zdecyduj, czy należy używać dodatku narzędzi VSTO dla programów lub dodatku pakietu Office.|[Harmonogram działania dla dodatków pakietu Office, VSTO i VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|
|Tworzenie dodatku narzędzi VSTO dla programów.|[Tworzenie dodatków narzędzi VSTO dla programów, za pomocą programu Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

##  <a name="Solutions"></a> Tworzenie rozwiązań programu SharePoint
 Tworzenie rozwiązań programu SharePoint pod kątem programu SharePoint Foundation 2010 i SharePoint Server 2010 lub rozszerzyć programu SharePoint 2013 i programu SharePoint 2016 w sposób poza to, co można zrobić za pomocą dodatku programu SharePoint.

 Rozwiązania programu SharePoint wymagają serwery farmy programu SharePoint w środowisku lokalnym. Administratorzy muszą zainstalować je, a ponieważ rozwiązań w programie SharePoint, mogą one wpłynąć na wydajność serwera. Jednak rozwiązania zapewniają lepszy dostęp do obiektów programu SharePoint. Ponadto w przypadku tworzenia rozwiązania programu SharePoint, możesz korzystać z programu .NET Framework i używać języka C# i Visual Basic do interakcji z obiektami programu SharePoint.

 **Dowiedz się więcej**

|Zadanie|Zobacz|
|--------|---------|
|Porównanie rozwiązań programu SharePoint przy użyciu dodatków programu SharePoint.|[Dodatków programu SharePoint w porównaniu z rozwiązaniami SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Tworzenie rozwiązań programu SharePoint.|[Tworzenie rozwiązań SharePoint](../sharepoint/create-sharepoint-solutions.md)|
