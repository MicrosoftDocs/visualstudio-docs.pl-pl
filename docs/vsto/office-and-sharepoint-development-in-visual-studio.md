---
title: Programowanie dla pakietu Office i programu SharePoint w programie Visual Studio
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
ms.openlocfilehash: ce0084d6bf734ee8a9de63b0cf3da73504b0d4e4
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800947"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Programowanie dla pakietu Office i programu SharePoint w programie Visual Studio
  Możesz rozciągnąć Microsoft Office i SharePoint, tworząc lekkie aplikacje lub dodatki pobierane przez użytkowników ze [sklepu Office](https://store.office.com/) lub wykazu organizacji lub tworząc rozwiązanie oparte na .NET Framework, które użytkownicy instalują na komputerze.

 W tym temacie:

- [Twórz Dodatki dla pakietu Office i programu SharePoint](#Apps)

- [Tworzenie dodatku narzędzi VSTO](#Add-ins)

- [Utwórz rozwiązanie SharePoint](#Solutions)

## <a name="create-add-ins-for-office-and-sharepoint"></a><a name="Apps"></a> Twórz Dodatki dla pakietu Office i programu SharePoint
 Pakiety Office 2013 i SharePoint 2013 wprowadzają nowy model dodatków, który ułatwia tworzenie, dystrybuowanie i zarabiaj dodatków, które poszerzają pakiet Office i program SharePoint.  Te dodatki mogą działać w pakiecie Office lub SharePoint Online, a użytkownicy mogą z nich korzystać z wielu urządzeń.

 Dowiedz się, jak korzystać z nowego [modelu dodatków pakietu Office](/office/dev/add-ins/overview/office-add-ins) , aby zwiększyć możliwości pakietu Office dla użytkowników.

 Te dodatki mają niewielkie rozmiary w porównaniu z dodatkami i rozwiązaniami programu VSTO i można je skompilować przy użyciu prawie dowolnej technologii programowania sieci Web, takiej jak HTML5, JavaScript, CSS3 i XML.  Aby rozpocząć, użyj Office Developer Tools w programie Visual Studio, który umożliwia tworzenie projektów, pisanie kodu i uruchamianie dodatków w przeglądarce.

 ![Aplikacje dla pakietu Office i modelu koncepcyjnego programu SharePoint](../vsto/media/officeandsharepointapps2015.png "Aplikacje dla pakietu Office i modelu koncepcyjnego programu SharePoint")

### <a name="build-an-office-add-in"></a>Tworzenie dodatku dla pakietu Office
 Aby zwiększyć funkcjonalność pakietu Office, skompiluj dodatek pakietu Office. Zasadniczo jest to strona sieci Web, która jest hostowana w aplikacji pakietu Office, takiej jak Excel, Word, Outlook i PowerPoint. Aplikacja może dodawać funkcje do dokumentów, arkuszy, wiadomości e-mail, terminów, prezentacji i projektów.

 Możesz sprzedawać swoją aplikację w sklepie Office.  [Sklep Office](https://store.office.com/) ułatwia Zarabiaj dodatków, zarządzanie aktualizacjami i śledzenie danych telemetrycznych. Możesz również opublikować aplikację dla użytkowników za poorednictwem wykazu aplikacji w programie SharePoint lub w programie Exchange Server.

 Następująca aplikacja dla pakietu Office pokazuje dane arkusza na mapie Bing.

 ![Aplikacja zawartości dla pakietu Office](../vsto/media/appforoffice.png "Aplikacja zawartości dla pakietu Office")

 **Dowiedz się więcej**

|Działanie|Zobacz|
|--------|---------|
|Dowiedz się więcej na temat dodatków pakietu Office, a następnie Skompiluj ją.|[Dodatki pakietu Office](/office/dev/add-ins/publish/publish)|
|Porównaj różne sposoby, w których można zwiększyć pakiet Office i zdecydować, czy należy użyć aplikacji, czy dodatku pakietu Office.|[Plan dla dodatków pakietu Office, narzędzi VSTO i VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|

### <a name="build-a-sharepoint-add-in"></a>Tworzenie dodatku programu SharePoint
 Aby zwiększyć SharePoint dla użytkowników, należy utworzyć dodatek programu SharePoint. Zasadniczo jest to niewielka, łatwa w użyciu, samodzielna aplikacja, która rozwiązuje potrzeby dla użytkowników lub firmy.

 Możesz sprzedawać aplikację dla programu SharePoint w [sklepie Office](https://store.office.com/). Dodatek można także opublikować użytkownikom za poorednictwem wykazu dodatków w programie SharePoint.  Właściciele witryny mogą instalować, uaktualniać i odinstalowywać dodatek w swoich witrynach programu SharePoint bez pomocy serwera farmy lub administratora zbioru witryn.

 Oto przykład aplikacji dla programu SharePoint, która ułatwia użytkownikom zarządzanie kontaktami biznesowymi.

 ![Aplikacja Business Contact Manager dla programu SharePoint](../vsto/media/appforsharepoint.png "Aplikacja Business Contact Manager dla programu SharePoint")

 **Dowiedz się więcej**

|Działanie|Zobacz|
|--------|---------|
|Dowiedz się więcej o dodatkach programu SharePoint, a następnie Skompiluj je.|[Dodatki programu SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|Porównaj Dodatki dla programu SharePoint z tradycyjnymi rozwiązaniami programu SharePoint.|[Dodatki programu SharePoint porównane z rozwiązaniami programu SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Zdecyduj, czy chcesz skompilować dodatek programu SharePoint, czy rozwiązanie programu SharePoint.|[Podejmowanie decyzji między dodatkami programu SharePoint i rozwiązaniami programu SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="create-a-vsto-add-in"></a><a name="Add-ins"></a> Tworzenie dodatku narzędzi VSTO
 Utwórz dodatek narzędzi VSTO dla pakietu Office 2007 lub pakietu Office 2010 lub rozszerzenia pakietu Office 2013 i pakietu Office 2016 poza możliwościami dotyczącymi dodatków pakietu Office. Dodatki narzędzi VSTO są uruchamiane tylko na pulpicie. Użytkownicy muszą instalować dodatki narzędzi VSTO, aby były zazwyczaj trudniejsze do wdrożenia i obsługi.  Jednak dodatek VSTO może być ściśle zintegrowany z pakietem Office. Na przykład może dodawać karty i kontrolki do wstążki pakietu Office oraz wykonywać zaawansowane zadania automatyzacji, takie jak scalanie dokumentów lub modyfikowanie wykresów. Możesz użyć .NET Framework i Visual Basic do współdziałania z obiektami pakietu Office.

 Oto przykład możliwości dodatku VSTO. Ten dodatek narzędzi VSTO dodaje kontrolki wstążki, niestandardowe okienko zadań i okno dialogowe do programu PowerPoint.

 ![Rozwiązanie dodatku dla programu PowerPoint](../vsto/media/powerpointaddin.png "Rozwiązanie dodatku dla programu PowerPoint")

 **Dowiedz się więcej**

|Działanie|Odczyt|
|--------|----------|
|Porównaj różne sposoby, w których można zwiększyć pakiet Office i zdecydować, czy należy użyć dodatku VSTO lub dodatku dla pakietu Office.|[Plan dla dodatków pakietu Office, narzędzi VSTO i VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|
|Utwórz dodatek narzędzi VSTO.|[Kompilacja dodatków VSTO przy użyciu programu Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="create-a-sharepoint-solution"></a><a name="Solutions"></a> Utwórz rozwiązanie SharePoint
 Utwórz rozwiązanie SharePoint dla obiektów docelowych SharePoint Foundation 2010 i SharePoint Server 2010 lub w celu zwiększenia możliwości programu SharePoint 2013 i SharePoint 2016 w sposób wykraczający poza to, co jest możliwe w przypadku dodatku programu SharePoint.

 Rozwiązania programu SharePoint wymagają lokalnych serwerów farmy programu SharePoint. Administratorzy muszą je zainstalować, a ponieważ rozwiązania są wykonywane w programie SharePoint, mogą mieć wpływ na wydajność serwera. Jednak rozwiązania zapewniają lepszy dostęp do obiektów programu SharePoint. Ponadto podczas tworzenia rozwiązania programu SharePoint można korzystać z .NET Framework i używać języka C# i Visual Basic do współpracy z obiektami programu SharePoint.

 **Dowiedz się więcej**

|Działanie|Zobacz|
|--------|---------|
|Porównaj rozwiązania programu SharePoint z dodatkami programu SharePoint.|[Dodatki programu SharePoint porównane z rozwiązaniami programu SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Utwórz rozwiązanie SharePoint.|[Tworzenie rozwiązań SharePoint](../sharepoint/create-sharepoint-solutions.md)|
