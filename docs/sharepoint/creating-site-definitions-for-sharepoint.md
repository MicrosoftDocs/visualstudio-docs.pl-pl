---
title: Tworzenie definicji witryny programu SharePoint | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2abf61bbc960e342a395e9c0ff3395ecde852137
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604873"
---
# <a name="create-site-definitions-for-sharepoint"></a>Tworzenie definicji witryny dla SharePoint
  Projekt definicji witryny programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umożliwia tworzenie *definicji witryny*, który służy jako podstawa nową witrynę programu SharePoint. Te definicje określić nie tylko wyglądu i zachowania witryny programu SharePoint, ale również jego domyślnej zawartości i funkcji. W definicji można umieścić wstępnie skonfigurowanej listy, typy zawartości, odbiorcy zdarzeń, obrazów i innych elementów. Program SharePoint zawiera niektóre definicje witryn, blogów, np. na przykład. Podczas tworzenia witryny, na podstawie definicji witryny blogów lokacja zawiera listy, składniki Web Part i inne elementy, które wymaga lokacji do obsługi blogów.

 Aby uzyskać więcej informacji na temat definicji witryny zobacz [definicje i szablony witryn](http://go.microsoft.com/fwlink/?LinkId=179134).

## <a name="site-definition-projects"></a>Witryna definicji projektów
 Witryna definicji projektów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Podaj tylko podstawowe pliki, których potrzebuje witryny programu SharePoint, przy czym nie udostępniają one wszystkie funkcje domyślne. Należy dodać pliki i zawartości oferują funkcje, które chcesz. Witryny można tworzyć ręcznie, tworząc i dodanie plików, które są potrzebne.

## <a name="feature-stapling"></a>Zszywanie funkcji
 Jedną z zalet Tworzenie definicji witryny w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jest będą automatycznie używać *Zszywanie funkcji*. Zszywanie funkcji dołącza funkcję do definicji lokacji zamiast osadzania ich funkcji w definicji witryny. W ten sposób pozwala na dodawanie funkcji do żadnej lokacji utworzone przy użyciu definicji witryny bez modyfikowania oryginalnej definicji witryny. Aby uzyskać więcej informacji, zobacz [Zszywanie funkcji](http://go.microsoft.com/fwlink/?LinkID=119283).

## <a name="site-definition-project-components"></a>Definicje witryny składników projektu
 Podczas tworzenia rozwiązania definicji witryny następujące domyślne pliki są dodawane do jej **SiteDefinition** węzła.

|Nazwa pliku|Opis|
|---------------|-----------------|
|*default.aspx*|Domyślną stronę główną ASPX dla nowej witryny programu SharePoint.|
|*onet.xml*|Określa konfigurację nowej lokacji, składniki szablonu definicji witryny i zachowanie domyślne. Te ustawienia można obejmować atrybuty takie jak typy zawartości, które są włączone, domyślne widoki listy plików szablonów dokumentów i składniki Web Part dołączone do lokacji. Domyślnie `Modules` sekcja zawiera listę plików, które mają zostać dodane do witryny programu SharePoint i sposobu ich konfiguracji.|
|*webtemp_\<SiteDefinitionName>.xml*|Określa konfiguracje definicji witryny, które pojawia się w **wybór szablonu** części **nową witrynę programu SharePoint** strony.|

 Domyślnie wszystkie definicje lokacji są przechowywane w  *\<dysku: > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* folderu. Każda definicja lokacji ma swój własny podfolderu.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Tworzenie podstawowego projektu definicji witryny](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Prowadzi użytkownika krok po kroku proces tworzenia podstawowego projektu definicji witryny w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Instrukcje: Utwórz niestandardową witrynę definicji i konfiguracji](http://go.microsoft.com/fwlink/?LinkId=183309)|Opisuje sposób tworzenia definicji witryny niestandardowej w programie SharePoint przez kopiowanie istniejącej definicji witryny i następnie modyfikując kopię.|
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|W tym artykule opisano oryginalnego pliku, który określa dostępne w definicji witryny **wybór szablonu** części **nową witrynę programu SharePoint** strony.|
|[Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|W tym artykule opisano sposób przygotowania rozwiązania programu SharePoint do użytku globalnego.|
|[Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|W tym artykule opisano, jak można utworzyć części strony programu SharePoint, które użytkownicy mogą modyfikować.|
|[Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|W tym artykule opisano sposób tworzenia kontrolek wielokrotnego użytku, które działają w stronach aplikacji oraz składników Web Part.|
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|W tym artykule opisano sposób korzystania z projektanta, który pojawia się po otwarciu strony sieci Web w projekcie.|
|[ASP.NET Web Pages — omówienie](http://go.microsoft.com/fwlink/?LinkId=178726)|Zawiera ogólne informacje o strukturze [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony sieci Web, w jaki strony są przetwarzane przez [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]i w jaki sposób [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stronach są wyświetlane znaczników, który jest zgodny ze standardami XHTML.|
|[Składnia strony sieci Web platformy ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|W tym artykule opisano elementy znaczników, które składają się na stronie ASP.NET.|
|[Programowanie wzorca ASP.NET Web Pages](http://go.microsoft.com/fwlink/?LinkId=178728)|Zawiera informacje o sposobie tworzenia procedury obsługi zdarzeń w [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stron oraz sposób pracy ze skryptem klienta.|
|[Programowanie w programie Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Opisuje sposób używania modelu obiektu zarządzanego, który znajduje się w [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|

## <a name="see-also"></a>Zobacz także
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
