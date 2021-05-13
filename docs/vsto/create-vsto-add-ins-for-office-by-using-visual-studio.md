---
title: Tworzenie dodatków narzędzi VSTO dla pakietu Office w programie Visual Studio
description: Dowiedz się, jak za pomocą Microsoft Office programistów w programie Visual Studio tworzyć .NET Framework, które rozszerzają pakiet Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 990caeec642a745bec5b6e0f2d29ff5d6213d095
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848321"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Tworzenie dodatków narzędzi VSTO dla pakietu Office w programie Visual Studio
> [!IMPORTANT]
> VSTO opiera się na [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Dodatki COM można również zapisywać za pomocą .NET Framework. Dodatków pakietu Office nie można tworzyć za pomocą [programu .NET Core i .NET 5+](https://docs.microsoft.com/dotnet/core/dotnet-five), najnowszych wersji programu .NET. Jest to spowodowane tym, że program .NET Core/.NET 5+ nie może współpracować z programem .NET Framework w tym samym procesie i może prowadzić do błędów ładowania dodatków. Możesz nadal używać usługi .NET Framework do pisania dodatków VSTO i COM dla pakietu Office. Firma Microsoft nie będzie aktualizować usługi VSTO ani platformy dodatku COM w celu używania platformy .NET Core lub .NET 5+. Możesz skorzystać z programu .NET Core i .NET 5+, w tym programu ASP.NET Core, aby utworzyć stronę serwera dodatków internetowych [pakietu Office.](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)

  Aby tworzyć aplikacje Microsoft Office, które rozszerzają pakiet Office, Visual Studio tworzyć aplikacje .NET Framework narzędzia deweloperskie w programie . Te aplikacje są również nazywane *rozwiązaniami pakietu Office.*

 Narzędzia deweloperskie pakietu Office zapewniają funkcje, które ułatwiają tworzenie rozwiązań pakietu Office, które odpowiadają na różne potrzeby biznesowe. Narzędzia obejmują szablony projektów, które ułatwiają tworzenie rozwiązań pakietu Office przy użyciu programu Visual Basic lub Visual C# oraz wizualnych projektantów, którzy ułatwiają tworzenie niestandardowych interfejsów użytkownika dla rozwiązań pakietu Office.

[!include[Add-ins note](includes/addinsnote.md)]

 Aby uzyskać najnowsze informacje na temat tworzenia aplikacji dla pakietu Office, zobacz [centrum deweloperów Microsoft Office office.](https://developer.microsoft.com/office/docs)

## <a name="in-this-section"></a>W tej sekcji
- [Wprowadzenie do tworzenia &#40;Office w usłudze Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)

 Zawiera linki do informacji na temat sposobu konfigurowania komputera dewelopera w celu tworzenia rozwiązań pakietu Office, rozpoczynania tworzenia rozwiązań pakietu Office oraz nowości w zakresie tworzenia aplikacji pakietu Office w Visual Studio.

- [Uaktualnianie i migrowanie rozwiązań pakietu Office](upgrading-and-migrating-office-solutions.md)

 Zawiera linki do informacji o procesie uaktualniania projektów utworzonych przy użyciu wcześniejszych wersji Visual Studio.

- [Architektura rozwiązań pakietu Office w Visual Studio](architecture-of-office-solutions-in-visual-studio.md)

 Zawiera linki do informacji na temat sposobu działania rozwiązań pakietu Office, w tym informacji o dostosowaniach na poziomie dokumentu i dodatków VSTO.

- [Projektowanie i tworzenie rozwiązań pakietu Office](designing-and-creating-office-solutions.md)

 Zawiera informacje na temat sposobu tworzenia projektu pakietu Office i konfigurowania projektu w Visual Studio.

- [Opracowywanie rozwiązań pakietu Office](developing-office-solutions.md)

 Zawiera informacje na temat sposobu używania kodu zarządzanego z rozwiązaniami pakietu Office, w tym sposobu dostosowywania interfejsu użytkownika pakietu Office, pracy z danymi i rozwiązywania problemów.

- [Rozwiązania programu Excel](excel-solutions.md)

 Zawiera informacje na temat automatyzowania programu Excel, tworzenia rozwiązań programu Excel i zrozumienia problemów z globalizacją specyficznych dla programu Excel.

- [Rozwiązania InfoPath](infopath-solutions.md)

 Zawiera informacje na temat tworzenia szablonów formularzy i dodatków VSTO dla programu InfoPath.

- [Rozwiązania programu Outlook](outlook-solutions.md)

 Ten temat zawiera informacje na temat automatyzowania programu Outlook i tworzenia dodatków VSTO programu Outlook oraz regionów formularzy.

- [Rozwiązania programu PowerPoint](powerpoint-solutions.md)

 Ten temat zawiera informacje na temat automatyzowania programu PowerPoint i tworzenia dodatków VSTO programu PowerPoint.

- [Rozwiązania projektu](project-solutions.md)

 Zawiera informacje o tym, jak zautomatyzować Microsoft Office projektu i tworzyć dodatki VSTO projektu.

- [Rozwiązania programu Visio](visio-solutions.md)

 Ten temat zawiera informacje na temat automatyzowania programu Visio i tworzenia dodatków narzędzi VSTO programu Visio.

- [Rozwiązania programu Word](word-solutions.md)

 Zawiera informacje na temat automatyzowania programu Word i tworzenia rozwiązań programu Word.

- [Tworzenie rozwiązań pakietu Office](building-office-solutions.md)

 Zawiera informacje o różnicach między tworzeniem projektów pakietu Office i innymi typami projektów w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Debugowanie projektów pakietu Office](debugging-office-projects.md)

 Zawiera informacje o różnicach między debugowaniem projektów pakietu Office i innymi typami projektów w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Zabezpieczanie rozwiązań pakietu Office](securing-office-solutions.md)

 Zawiera informacje na temat sposobu działania funkcji zabezpieczeń w rozwiązaniach pakietu Office.

- [Wdrażanie rozwiązania pakietu Office](deploying-an-office-solution.md)

 Zawiera informacje na temat sposobu, w jaki rozwiązania pakietu Office mają być dostępne dla użytkowników, oraz głównych problemów, które należy wziąć pod uwagę podczas wyboru metody wdrażania.

- [Office development samples and walkthroughs (Przykłady i wskazówki dotyczące tworzenia aplikacji pakietu Office)](office-development-samples-and-walkthroughs.md)

 Zawiera linki do przykładowych aplikacji i tematów, które zawierają instrukcje krok po kroku dotyczące wykonywania typowych zadań.

- [Ogólne informacje na &#40;Office w programie Visual Studio&#41;](general-reference-office-development-in-visual-studio.md)

 Zawiera linki do szczegółowych informacji o podstawowych zestawach międzyopłaciowych pakietu Office, manifestach, elementach interfejsu użytkownika i komunikatach o błędach.

- [Zarządzana &#40;tworzenia pakietu Office w Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md)

 Zawiera linki do informacji o przestrzeniach nazw interfejsu API i typach używanych w projektach pakietu Office, które są kierowane do usługi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Dokumentacja referencyjna interfejsu API dotycząca przestrzeni nazw i typów używanych w projektach pakietu Office, które są kierowane do usługi .NET Framework 3.5, znajduje się w następującej sekcji referencyjnej w dokumentacji programu Visual Studio 2008: Dokumentacja zarządzana systemu [2007](managed-reference-office-development-in-visual-studio.md).

- [Nieza zarządzanie interfejsem API w &#40;Office w usłudze Visual Studio&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Zawiera linki do informacji o interfejsach COM, których można użyć do wykonywania akcji, takich jak ładowanie i zwalnianie zarządzanych dodatków VSTO w aplikacjach pakietu Office.

## <a name="related-sections"></a>Powiązane sekcje
- [Tworzenie aplikacji pakietu Office za Visual Studio portalu dla deweloperów](https://developer.microsoft.com/office/docs) Udostępnia dodatkowe zasoby, takie jak artykuły techniczne, filmy wideo i blogi.

- [Visual Studio centrum deweloperów](https://visualstudio.microsoft.com/) Udostępnia dodatkowe Visual Studio zasobów, takich jak artykuły techniczne, filmy wideo i blogi.

- [Microsoft Office deweloperskiej biblioteki MSDN](/previous-versions/office/office-12/bb726434(v=office.12)) Obszar biblioteki MSDN, w którym można znaleźć artykuły i dokumentację referencyjną dotyczącą opracowywania rozwiązań dla kilku wersji pakietu Office (nie jest to specyficzne dla tworzenia aplikacji pakietu Office przy użyciu Visual Studio).

- [Tworzenie aplikacji w Visual Studio](/previous-versions/h8w79z10(v=vs.140)) Zawiera linki do tematów, które wyjaśniają, jak używać programu Visual Studio do projektowania, opracowywania, debugowania i wdrażania aplikacji internetowych, usług internetowych XML i tradycyjnych aplikacji klienckich.

- [.NET Framework programistyczne w programie Visual Studio](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) W tym artykule omówiono tworzenie aplikacji za pomocą .NET Framework w Visual Basic i Visual C#.
