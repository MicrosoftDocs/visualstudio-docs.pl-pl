---
title: Visual Studio SDK | Microsoft Docs
description: Zestaw Visual Studio SDK ułatwia poszerzanie funkcji i dodawanie nowych funkcji do programu Visual Studio. Dowiedz się więcej na temat sposobów, w których można rozciągnąć program Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91411ec183e6c51abd825af1080c4330ca46fc90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062528"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Zestaw Visual Studio SDK ułatwia poszerzanie funkcji programu Visual Studio lub integrowanie nowych funkcji w programie Visual Studio. Rozszerzenia można dystrybuować do innych użytkowników, a także do Visual Studio Marketplace. Poniżej przedstawiono kilka sposobów, w których można rozciągnąć program Visual Studio:

- Dodawanie poleceń, przycisków, menu i innych elementów interfejsu użytkownika do IDE

- Dodawanie okien narzędzi do nowych funkcji

- Rozszerzając funkcję IntelliSense dla danego języka lub Udostępnij technologię IntelliSense dla nowych języków programowania

- Korzystanie z żarówki w celu zapewnienia wskazówek i sugestii, które ułatwiają deweloperom pisanie lepszego kodu

- Włączanie obsługi nowego języka

- Dodaj niestandardowy typ projektu

- Dotrzej do milionów deweloperów za pośrednictwem Visual Studio Marketplace

  Jeśli jeszcze nie zapisano rozszerzenia programu Visual Studio, należy znaleźć więcej informacji na temat tych funkcji i w momencie [rozpoczęcia tworzenia rozszerzeń programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Instalowanie zestawu Visual Studio SDK
 Visual Studio SDK to opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-sdk"></a>Co nowego w zestawie SDK programu Visual Studio
 Zestaw Visual Studio SDK zawiera nowe funkcje, takie jak synchroniczne, automatyczne ładowanie rozszerzeń ostrzeżenie i format VSIX v3, a także istotne zmiany, które mogą wymagać aktualizacji rozszerzenia. Aby uzyskać więcej informacji, zobacz [co nowego w zestawie SDK programu Visual studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md) i [co nowego w zestawie SDK programu Visual Studio 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Wskazówki dotyczące środowiska użytkownika programu Visual Studio
 Uzyskaj doskonałe wskazówki dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [wytycznych dotyczących środowiska użytkownika programu Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 Możesz również dowiedzieć się, jak zwiększyć atrakcyjność rozszerzenia na urządzeniach o wysokiej rozdzielczości DPI z artykułem [problemy dotyczące adresów dpi](../extensibility/addressing-dpi-issues2.md) .

 Skorzystaj z [usługi Image Service i katalogu](../extensibility/image-service-and-catalog.md) , aby uzyskać doskonałe zarządzanie obrazami i obsługę wysokiej rozdzielczości DPI i ich obsługi.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Znajdź i zainstaluj istniejące rozszerzenia programu Visual Studio
 Rozszerzenia programu Visual Studio można znaleźć w oknie dialogowym **rozszerzenia i aktualizacje** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Możesz również znaleźć rozszerzenia w [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Dokumentacja zestawu Visual Studio SDK
 Informacje o interfejsie API zestawu SDK programu Visual Studio można znaleźć w [dokumentacji programu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK — przykłady
 Przykłady rozszerzeń typu "open source" w witrynie GitHub można znaleźć w przykładach [programu Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples). To repozytorium GitHub zawiera przykłady ilustrujące różne rozszerzalne funkcje w programie Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Inne zasoby programu Visual Studio SDK
 Jeśli masz pytania dotyczące VSSDK lub chcesz udostępnić swoje środowiska opracowywania rozszerzeń, możesz użyć [forum rozszerzeń programu Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) lub [ExtendVS warunkom chatroom](https://gitter.im/Microsoft/extendvs).

 Więcej informacji można znaleźć w [blogu VSX Arcana](/archive/blogs/vsx/) i wielu blogach pisanych przez firmę Microsoft MVP:

- [Ulubione rozszerzenia programu Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Rozszerzalność programu Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Rozszerzanie programu Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Zobacz też

- [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Często zadawane pytania: konwertowanie dodatków na rozszerzenia pakietu VSPackage](/previous-versions/visualstudio/visual-studio-2015/extensibility/faq-converting-add-ins-to-vspackage-extensions?preserve-view=true&view=vs-2015)
- [Zarządzanie wieloma wątkami w kodzie zarządzanym](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Poszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Dodawanie poleceń do pasków narzędzi](../extensibility/adding-commands-to-toolbars.md)
- [Rozbudowane i dostosowujące okna narzędzi](../extensibility/extending-and-customizing-tool-windows.md)
- [Rozszerzenia edytora i usługi językowej](../extensibility/editor-and-language-service-extensions.md)
- [Rozwiń projekty](../extensibility/extending-projects.md)
- [Rozwiń Ustawienia użytkownika i opcje](../extensibility/extending-user-settings-and-options.md)
- [Tworzenie niestandardowych szablonów projektów i elementów](../extensibility/creating-custom-project-and-item-templates.md)
- [Rozwiń właściwości i okno właściwości](../extensibility/extending-properties-and-the-property-window.md)
- [Rozszerzając inne części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Używanie i świadczenie usług](../extensibility/using-and-providing-services.md)
- [Zarządzanie pakietami VSPackage](../extensibility/managing-vspackages.md)
- [Powłoka izolowana programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Wyślij rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Wewnątrz zestawu Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Obsługa zestawu Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Dokumentacja zestawu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)