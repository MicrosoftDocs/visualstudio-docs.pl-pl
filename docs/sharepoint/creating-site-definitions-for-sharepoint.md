---
title: Tworzenie definicji witryny dla programu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a75b7143412d360a7663e7cf94a1244d66d15a2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984521"
---
# <a name="create-site-definitions-for-sharepoint"></a>Tworzenie definicji witryny dla programu SharePoint
  Projekt definicji witryny programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umożliwia utworzenie *definicji lokacji*, która służy jako podstawa dla nowej witryny programu SharePoint. Definicje te nie tylko określają wygląd i zachowanie witryny programu SharePoint, ale również jego domyślną zawartość i funkcje. W definicji można umieścić wstępnie skonfigurowane listy, typy zawartości, odbiorniki zdarzeń, obrazy i inne elementy. Program SharePoint zawiera definicje witryn, takie jak BLOG, na przykład. W przypadku tworzenia witryny na podstawie definicji witryny blogu lokacja zawiera listy, składniki Web Part i inne elementy wymagane przez witrynę blogów.

 Aby uzyskać więcej informacji na temat definicji lokacji, zobacz [Szablony i definicje witryn](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Projekty definicji lokacji
 Projekty definicji lokacji w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawierają tylko podstawowe pliki, których potrzebuje witryna programu SharePoint; nie zapewniają one żadnej domyślnej funkcji. Aby zapewnić żądaną funkcjonalność, należy dodać pliki i zawartość. Witrynę można utworzyć ręcznie, tworząc i dodając potrzebne pliki.

## <a name="feature-stapling"></a>Zszywanie funkcji
 Jedną z zalet tworzenia definicji lokacji w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jest automatyczne korzystanie z *funkcji zszywania*. Funkcja zszywania funkcji dołącza funkcję do definicji lokacji zamiast osadzania jej funkcji w samej definicji lokacji. Dzięki temu można dodać funkcję do dowolnej lokacji utworzonej przy użyciu definicji lokacji bez konieczności modyfikowania oryginalnej definicji lokacji. Aby uzyskać więcej informacji, zobacz [zszywanie funkcji](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Składniki projektu definicji witryny
 Podczas tworzenia rozwiązania definicji lokacji do jego węzła **sitedefinition** dodawane są następujące domyślne pliki.

|Nazwa pliku|Opis|
|---------------|-----------------|
|*default. aspx*|Domyślna strona główna ASPX dla nowej witryny programu SharePoint.|
|*onet. XML*|Określa konfigurację nowej lokacji, składników szablonu definicji lokacji i zachowania domyślnego. Te ustawienia mogą zawierać atrybuty, takie jak typy zawartości, które są włączone, domyślne widoki list, pliki szablonów dokumentów i składniki Web Part dołączone do witryny. Domyślnie sekcja `Modules` zawiera listę plików, które mają zostać dodane do witryny programu SharePoint i sposobu ich konfiguracji.|
|*webtemp_\<SiteDefinitionName >. XML*|Określa konfiguracje definicji lokacji, które pojawiają się w sekcji **Wybieranie szablonu** na **nowej stronie witryny programu SharePoint** .|

 Domyślnie wszystkie definicje lokacji są przechowywane na *dysku\<: > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* folder. Każda definicja lokacji ma własny podfolder.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Tworzenie podstawowego projektu definicji witryny](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Prowadzi krok po kroku przez tworzenie podstawowego projektu definicji lokacji w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Instrukcje: Tworzenie niestandardowej definicji lokacji i konfiguracji](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Opisuje sposób tworzenia niestandardowej definicji lokacji w programie SharePoint przez skopiowanie istniejącej definicji lokacji, a następnie zmodyfikowanie kopii.|
|[*WEBTEMP. XML*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Opisuje oryginalny plik, który określa definicje witryn dostępne w sekcji **Wybór szablonu** **nowej strony witryny programu SharePoint** .|
|[Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Opisuje sposób przygotowania rozwiązań programu SharePoint do użytku globalnego.|
|[Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Opisuje, jak można tworzyć części strony programu SharePoint, które użytkownicy mogą modyfikować.|
|[Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Opisuje sposób tworzenia formantów wielokrotnego użytku, które są uruchamiane na stronach aplikacji i składniki Web Part.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Opisuje, jak używać projektanta, który pojawia się po otwarciu strony sieci Web w projekcie.|
|[ASP.NET stron sieci Web — Omówienie](/previous-versions/aspnet/428509ah(v=vs.100))|Zawiera ogólne informacje o strukturze [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stron sieci Web, sposobie przetwarzania stron przez [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]i sposobie wyświetlania przez strony [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] znaczników, które są zgodne ze standardami XHTML.|
|[Składnia strony sieci Web ASP.NET](/previous-versions/aspnet/k33801s3(v=vs.100))|Opisuje elementy znaczników, które składają się na stronę ASP.NET.|
|[Programowanie stron sieci Web ASP.NET](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Zawiera informacje o sposobach tworzenia programów obsługi zdarzeń na stronach [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] i sposobach pracy z skryptem klienta programu.|
|[Programowanie w programie Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Opisuje sposób korzystania z modelu obiektów zarządzanych, który jest dostępny w [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|

## <a name="see-also"></a>Zobacz także
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
