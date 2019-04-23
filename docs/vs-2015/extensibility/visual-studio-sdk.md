---
title: Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c338648ebb69874781906c0eabff670e5158be8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050910"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK pomaga Rozszerz funkcje programu Visual Studio lub Zintegruj nowe funkcje do programu Visual Studio. Można dystrybuować swoje rozszerzenia innym użytkownikom, a także do galerii Visual Studio. Poniżej przedstawiono kilka sposobów, w którym można rozszerzyć Visual Studio:  
  
- Dodawanie poleceń, przyciski, menu i inne elementy interfejsu użytkownika do środowiska IDE  
  
- Dodaj okien narzędzi dla nowych funkcji  
  
- Rozszerzanie funkcji IntelliSense dla danego języka, lub udostępni funkcję IntelliSense dla nowych języków programowania  
  
- Użyj żarówki, aby zapewnić wskazówki i sugestie, które ułatwiają deweloperom pisanie kodu lepiej  
  
- Włącz obsługę nowy język  
  
- Dodawanie typu niestandardowego projektu  
  
- Dotrzyj do milionów deweloperów za pośrednictwem witryny Marketplace programu Visual Studio  
  
  Jeśli rozszerzenie programu Visual Studio przed nigdy nie zostały zapisane, znajdziesz więcej informacji o tych funkcjach i na [Rozpoczynanie tworzenia rozszerzeń programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalowanie programu Visual Studio SDK  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>What's New in Visual Studio 2015 SDK  
 Visual Studio SDK zawiera niektóre nowe funkcje, w tym żarówki i nowe elementy projektu, które pozwalają tworzyć polecenia menu, okien narzędzi i rozszerzenia edytora, przy użyciu pakietu VSIX. Aby uzyskać więcej informacji, zobacz [What's New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Wskazówki dotyczące interfejsu użytkownika w programie Visual Studio  
 Doskonałe porady dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [dotyczące środowiska użytkownika w usłudze Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Można także dowiesz się, jak tworzyć rozszerzenia wyglądał świetnie w wysokiej rozdzielczości DPI urządzeniami w usłudze naszych [adresowania problemów z technologią DPI](../extensibility/addressing-dpi-issues2.md) tematu.  
  
 Skorzystaj z zalet [Usługa obrazów i katalog](../extensibility/image-service-and-catalog.md) zarządzanie obrazami doskonałe i obsługę wysokiej rozdzielczości DPI i motywów.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Znajdowanie i instalowanie istniejących rozszerzeń programu Visual Studio  
 Można znaleźć rozszerzenia programu Visual Studio w **rozszerzenia i aktualizacje** dialog w **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Znajdowanie i przy użyciu rozszerzenia programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Możesz również znaleźć rozszerzenia w [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Dokumentacja zestawu Visual Studio SDK  
 Odwołanie interfejsu API zestawu SDK programu Visual Studio na można znaleźć [odwołanie do zestawu SDK programu Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Przykłady zestawu SDK programu Visual Studio  
 Przykłady "open source" z zestawu SDK rozszerzeń można znaleźć w witrynie GitHub pod [Visual Studio Samples](https://aka.ms/vs2015sdksamples). Tego repozytorium GitHub zawiera przykłady ilustrujące różne funkcje rozszerzonego w programie Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Inne zasoby zestawu SDK programu Visual Studio  
 Jeśli masz pytania dotyczące VSSDK lub chcesz udostępnić środowisko opracowywania rozszerzeń, możesz użyć [forum poświęcone programowi Visual Studio Extensibility](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) lub [Chat grupy ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Więcej informacji można znaleźć [blog VSX Arcana](http://blogs.msdn.com/b/vsx/) i liczbę blogi napisane przez MVPs firmy Microsoft:  
  
- [Favorite Visual Studio Extensions](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
- [Rozszerzanie programu Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [Rozszerzanie programu Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [FAQ: Konwertowanie dodatków na rozszerzenia pakietu VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Zarządzanie wieloma wątkami w kodzie zarządzanym](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [Dodawanie poleceń do pasków narzędzi](../extensibility/adding-commands-to-toolbars.md)   
 [Rozszerzanie i dostosowywanie narzędzi Windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [Edytora i rozszerzenia usługi w języka](../extensibility/editor-and-language-service-extensions.md)   
 [Rozszerzanie projektów](../extensibility/extending-projects.md)   
 [Rozszerzanie ustawień użytkownika ani opcji](../extensibility/extending-user-settings-and-options.md)   
 [Tworzenie szablonów elementów i projektów niestandardowych](../extensibility/creating-custom-project-and-item-templates.md)   
 [Rozszerzanie właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)   
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Korzystanie z usług i dostarczanie](../extensibility/using-and-providing-services.md)   
 [Rozszerzanie usług połączonych](../extensibility/extending-connected-services.md)   
 [Zarządzanie pakietami VSPackage](../extensibility/managing-vspackages.md)   
 [Program Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)   
 [Rozszerzenia programu Visual Studio wysyłki](../extensibility/shipping-visual-studio-extensions.md)   
 [W programie Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Obsługa programu Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archiwum](../extensibility/archive.md)   
 [Dokumentacja zestawu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
