---
title: Tworzenie definicji witryny dla programu SharePoint | Microsoft Docs
description: Utwórz definicje witryn dla programu SharePoint. Definicje lokacji określają wygląd i zachowanie witryny programu SharePoint oraz jej domyślnej zawartości i funkcji.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: 7585a4b80322afb37e816758fc7074806a443676
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850575"
---
# <a name="create-site-definitions-for-sharepoint"></a>Tworzenie definicji witryny dla programu SharePoint
  Projekt definicji witryny programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umożliwia utworzenie *definicji lokacji*, która służy jako podstawa dla nowej witryny programu SharePoint. Definicje te nie tylko określają wygląd i zachowanie witryny programu SharePoint, ale również jego domyślną zawartość i funkcje. W definicji można umieścić wstępnie skonfigurowane listy, typy zawartości, odbiorniki zdarzeń, obrazy i inne elementy. Program SharePoint zawiera definicje witryn, takie jak BLOG, na przykład. W przypadku tworzenia witryny na podstawie definicji witryny blogu lokacja zawiera listy, składniki Web Part i inne elementy wymagane przez witrynę blogów.

 Aby uzyskać więcej informacji na temat definicji lokacji, zobacz [Szablony i definicje witryn](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Projekty definicji lokacji
 Projekty definicji lokacji w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] udostępniają tylko podstawowe pliki, których potrzebuje witryna programu SharePoint. nie zapewniają one żadnej domyślnej funkcjonalności. Aby zapewnić żądaną funkcjonalność, należy dodać pliki i zawartość. Witrynę można utworzyć ręcznie, tworząc i dodając potrzebne pliki.

## <a name="feature-stapling"></a>Zszywanie funkcji
 Jedną z zalet tworzenia definicji lokacji w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jest automatyczne korzystanie z *funkcji zszywania*. Funkcja zszywania funkcji dołącza funkcję do definicji lokacji zamiast osadzania jej funkcji w samej definicji lokacji. Dzięki temu można dodać funkcję do dowolnej lokacji utworzonej przy użyciu definicji lokacji bez konieczności modyfikowania oryginalnej definicji lokacji. Aby uzyskać więcej informacji, zobacz [zszywanie funkcji](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Składniki projektu definicji witryny
 Podczas tworzenia rozwiązania definicji lokacji do jego węzła **sitedefinition** dodawane są następujące domyślne pliki.

|Nazwa pliku|Opis|
|---------------|-----------------|
|*default. aspx*|Domyślna strona główna ASPX dla nowej witryny programu SharePoint.|
|*onet.xml*|Określa konfigurację nowej lokacji, składników szablonu definicji lokacji i zachowania domyślnego. Te ustawienia mogą zawierać atrybuty, takie jak typy zawartości, które są włączone, domyślne widoki list, pliki szablonów dokumentów i składniki Web Part dołączone do witryny. Domyślnie `Modules` sekcja zawiera listę plików, które mają zostać dodane do witryny programu SharePoint i sposobu ich konfiguracji.|
|*webtemp_ \<SiteDefinitionName> . XML*|Określa konfiguracje definicji lokacji, które pojawiają się w sekcji **Wybieranie szablonu** na **nowej stronie witryny programu SharePoint** .|

 Domyślnie wszystkie definicje lokacji są przechowywane w folderze *\<drive:> \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* . Każda definicja lokacji ma własny podfolder.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: tworzenie podstawowego projektu definicji witryny](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Prowadzi krok po kroku przez tworzenie podstawowego projektu definicji lokacji w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Instrukcje: Tworzenie niestandardowej definicji lokacji i konfiguracji](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Opisuje sposób tworzenia niestandardowej definicji lokacji w programie SharePoint przez skopiowanie istniejącej definicji lokacji, a następnie zmodyfikowanie kopii.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Opisuje oryginalny plik, który określa definicje witryn dostępne w sekcji **Wybór szablonu** **nowej strony witryny programu SharePoint** .|
|[Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Opisuje sposób przygotowania rozwiązań programu SharePoint do użytku globalnego.|
|[Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Opisuje, jak można tworzyć części strony programu SharePoint, które użytkownicy mogą modyfikować.|
|[Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Opisuje sposób tworzenia formantów wielokrotnego użytku, które są uruchamiane na stronach aplikacji i składniki Web Part.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Opisuje, jak używać projektanta, który pojawia się po otwarciu strony sieci Web w projekcie.|
|[ASP.NET stron sieci Web — Omówienie](/previous-versions/aspnet/428509ah(v=vs.100))|Zawiera ogólne informacje dotyczące struktury [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stron sieci Web, sposobu przetwarzania stron przez [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] program oraz sposobu wyświetlania przez [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony znaczników, które są zgodne ze standardami XHTML.|
|[Składnia strony sieci Web ASP.NET](/previous-versions/aspnet/k33801s3(v=vs.100))|Opisuje elementy znaczników, które składają się na stronę ASP.NET.|
|[Programowanie stron sieci Web ASP.NET](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Zawiera informacje dotyczące sposobu tworzenia programów obsługi zdarzeń na [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stronach oraz sposobu pracy z skryptem klienta programu.|
|[Programowanie w programie Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Opisuje sposób korzystania z modelu obiektów zarządzanych, który jest dostępny w programie [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] .|

## <a name="see-also"></a>Zobacz także
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
