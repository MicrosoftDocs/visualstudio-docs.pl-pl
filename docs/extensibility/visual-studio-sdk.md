---
title: Zestaw SDK programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26ac42cbcc70c34b221f1146bb0ba5314ca104dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947749"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK pomaga Rozszerz funkcje programu Visual Studio lub Zintegruj nowe funkcje do programu Visual Studio. Można dystrybuować swoje rozszerzenia innym użytkownikom, a także do witryny Marketplace programu Visual Studio. Poniżej przedstawiono kilka sposobów, w którym można rozszerzyć Visual Studio:  
  
- Dodawanie poleceń, przyciski, menu i inne elementy interfejsu użytkownika do środowiska IDE  
  
- Dodaj okien narzędzi dla nowych funkcji  
  
- Rozszerzanie funkcji IntelliSense dla danego języka, lub udostępni funkcję IntelliSense dla nowych języków programowania  
  
- Użyj żarówki, aby zapewnić wskazówki i sugestie, które ułatwiają deweloperom pisanie kodu lepiej  
  
- Włącz obsługę nowy język  
  
- Dodawanie typu niestandardowego projektu  
  
- Dotrzyj do milionów deweloperów za pośrednictwem witryny Marketplace programu Visual Studio  
  
  Jeśli rozszerzenie programu Visual Studio przed nigdy nie zostały zapisane, znajdziesz więcej informacji o tych funkcjach i na [Rozpoczynanie tworzenia rozszerzeń programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="install-the-visual-studio-sdk"></a>Instalowanie zestawu Visual Studio SDK  
 Visual Studio SDK jest opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>What's new in Visual Studio 2017 SDK  
 Visual Studio SDK zawiera niektóre nowe funkcje, takie jak VSIX v3 format, jak również istotne zmiany, które mogą wymagać aktualizacji Twojego rozszerzenia. Aby uzyskać więcej informacji, zobacz [What's new in Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Dotyczące środowiska użytkownika w usłudze Visual Studio  
 Doskonałe porady dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [wskazówki dotyczące interfejsu użytkownika programu Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Można także dowiesz się, jak tworzyć rozszerzenia wyglądał świetnie w wysokiej rozdzielczości DPI urządzeniami w usłudze [wystawia DPI adres](../extensibility/addressing-dpi-issues2.md) artykułu.  
  
 Skorzystaj z zalet [obrazów usługi oraz katalogu](../extensibility/image-service-and-catalog.md) zarządzanie obrazami doskonałe i obsługę wysokiej rozdzielczości DPI i motywów.  
  
## <a name="find-and-install-existing-visual-studio-extensions"></a>Znajdź i zainstaluj istniejących rozszerzeń programu Visual Studio  
 Można znaleźć rozszerzenia programu Visual Studio w **rozszerzenia i aktualizacje** dialog w **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Znajdź i rozszerzenia programu Visual Studio użyj](../ide/finding-and-using-visual-studio-extensions.md). Możesz również znaleźć rozszerzenia w [witryny marketplace programu Visual Studio](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Odwołanie w Visual Studio SDK  
 Odwołanie interfejsu API zestawu SDK programu Visual Studio na można znaleźć [odwołanie do zestawu SDK programu Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Przykłady Visual Studio SDK  
 Przykłady "open source" z zestawu SDK rozszerzeń można znaleźć w witrynie GitHub pod [Visual Studio Samples](https://aka.ms/vs2015sdksamples). Tego repozytorium GitHub zawiera przykłady ilustrujące różne funkcje rozszerzonego w programie Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Inne zasoby programu Visual Studio SDK  
 Jeśli masz pytania dotyczące VSSDK lub chcesz udostępnić środowisko opracowywania rozszerzeń, możesz użyć [forum poświęcone programowi Visual Studio Extensibility](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) lub [pokoju dotyczącym oprogramowania Gitter ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Można znaleźć więcej informacji w [blog VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) i liczbę blogi napisane przez MVPs firmy Microsoft:  
  
-   [Ulubione rozszerzenia programu Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Rozszerzeń programu Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Rozszerzanie programu Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Zobacz także  
 [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [FAQ: Konwertowanie dodatków na rozszerzenia pakietu VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Zarządzanie wieloma wątkami w kodzie zarządzanym](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Rozszerzenie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [Dodawanie poleceń do pasków narzędzi](../extensibility/adding-commands-to-toolbars.md)   
 [Rozszerzanie i dostosowywanie narzędzi systemu windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [Edytor i język rozszerzenia usługi](../extensibility/editor-and-language-service-extensions.md)   
 [Rozszerzanie projektów](../extensibility/extending-projects.md)   
 [Rozszerzenie Opcje i ustawienia użytkownika](../extensibility/extending-user-settings-and-options.md)   
 [Tworzenie niestandardowych szablonów projektów i elementów](../extensibility/creating-custom-project-and-item-templates.md)   
 [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)   
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Korzystanie z usług i dostarczanie](../extensibility/using-and-providing-services.md)   
 [Zarządzanie pakietami VSPackage](../extensibility/managing-vspackages.md)   
 [Programu Visual Studio isolated shell](/visualstudio/extensibility/shell/visual-studio-isolated-shell)   
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [W programie Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Obsługa programu Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archiwum](../extensibility/archive.md)   
 [Odwołanie w Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
