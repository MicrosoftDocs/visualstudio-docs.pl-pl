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
ms.openlocfilehash: 27dce16d9fe02063eae935af96c26184285e583d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850379"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw Visual Studio SDK ułatwia poszerzanie funkcji programu Visual Studio lub integrowanie nowych funkcji w programie Visual Studio. Rozszerzenia można dystrybuować do innych użytkowników, a także do galerii programu Visual Studio. Poniżej przedstawiono kilka sposobów, w których można rozciągnąć program Visual Studio:  
  
- Dodawanie poleceń, przycisków, menu i innych elementów interfejsu użytkownika do IDE  
  
- Dodawanie okien narzędzi do nowych funkcji  
  
- Rozszerzając funkcję IntelliSense dla danego języka lub Udostępnij technologię IntelliSense dla nowych języków programowania  
  
- Korzystanie z żarówki w celu zapewnienia wskazówek i sugestii, które ułatwiają deweloperom pisanie lepszego kodu  
  
- Włączanie obsługi nowego języka  
  
- Dodaj niestandardowy typ projektu  
  
- Dotrzej do milionów deweloperów za pośrednictwem Visual Studio Marketplace  
  
  Jeśli jeszcze nie zapisano rozszerzenia programu Visual Studio, należy znaleźć więcej informacji na temat tych funkcji i w momencie [rozpoczęcia tworzenia rozszerzeń programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalowanie zestawu Visual Studio SDK  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Co nowego w zestawie SDK programu Visual Studio 2015  
 Zestaw Visual Studio SDK zawiera nowe funkcje, w tym żarówki i nowe elementy projektu, które umożliwiają tworzenie poleceń menu, okien narzędzi i rozszerzeń edytora przy użyciu pakietu VSIX. Aby uzyskać więcej informacji, zobacz [What's New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Wskazówki dotyczące interfejsu użytkownika w programie Visual Studio  
 Doskonałe porady dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [dotyczące środowiska użytkownika w usłudze Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Możesz również dowiedzieć się, jak zwiększyć atrakcyjność rozszerzenia na urządzeniach o wysokiej rozdzielczości DPI z tematem [Rozwiązywanie problemów dotyczących rozdzielczości DPI](../extensibility/addressing-dpi-issues2.md) .  
  
 Skorzystaj z [usługi Image Service i katalogu](../extensibility/image-service-and-catalog.md) , aby uzyskać doskonałe zarządzanie obrazami i obsługę wysokiej rozdzielczości DPI i ich obsługi.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Znajdowanie i Instalowanie istniejących rozszerzeń programu Visual Studio  
 Rozszerzenia programu Visual Studio można znaleźć w oknie dialogowym **rozszerzenia i aktualizacje** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Znajdowanie i przy użyciu rozszerzenia programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Możesz również znaleźć rozszerzenia w [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Dokumentacja zestawu Visual Studio SDK  
 Informacje o interfejsie API zestawu SDK programu Visual Studio można znaleźć w [dokumentacji programu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK — przykłady  
 Przykłady rozszerzeń typu "open source" w witrynie GitHub można znaleźć w przykładach [programu Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples). To repozytorium GitHub zawiera przykłady ilustrujące różne rozszerzalne funkcje w programie Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Inne zasoby programu Visual Studio SDK  
 Jeśli masz pytania dotyczące VSSDK lub chcesz udostępnić swoje środowiska opracowywania rozszerzeń, możesz użyć [forum rozszerzalności programu Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) lub [rozmowy z grupą ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Więcej informacji można znaleźć w [blogu VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) i wielu blogach pisanych przez firmę Microsoft MVP:  
  
- [Ulubione rozszerzenia programu Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)  
  
- [Rozszerzalność programu Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [Rozszerzanie programu Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Często zadawane pytania: konwertowanie dodatków na rozszerzenia pakietu vspackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Zarządzanie wieloma wątkami w kodzie zarządzanym](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)   
 [Dodawanie poleceń do pasków narzędzi](../extensibility/adding-commands-to-toolbars.md)   
 [Rozszerzanie i dostosowywanie narzędzi  systemu Windows](../extensibility/extending-and-customizing-tool-windows.md)  
 [Rozszerzenia edytora i usługi językowej](../extensibility/editor-and-language-service-extensions.md)   
 [Rozszerzanie projektów](../extensibility/extending-projects.md)   
 [Rozszerzanie ustawień użytkownika i opcji](../extensibility/extending-user-settings-and-options.md)   
 [Tworzenie niestandardowych szablonów projektów i elementów](../extensibility/creating-custom-project-and-item-templates.md)   
 [Rozszerzanie właściwości i okna właściwości](../extensibility/extending-properties-and-the-property-window.md)   
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Używanie i świadczenie usług](../extensibility/using-and-providing-services.md)   
 [Rozszerzanie połączonych usług](../extensibility/extending-connected-services.md)   
 [Zarządzanie  pakietów VSPackage](../extensibility/managing-vspackages.md)  
   [powłoka izolowana programu Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
 [Wysyłka rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [W  Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)  
 [Obsługa zestawu SDK programu Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
   [archiwalny](../extensibility/archive.md)  
 [Dokumentacja zestawu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
