---
title: Visual Studio SDK | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698073"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK pomaga rozszerzyć funkcje programu Visual Studio lub zintegrować nowe funkcje do programu Visual Studio. Rozszerzenia można rozpowszechniać wśród innych użytkowników, a także do portalu Visual Studio Marketplace. Oto niektóre ze sposobów, w jaki można rozszerzyć program Visual Studio:

- Dodawanie poleceń, przycisków, menu i innych elementów interfejsu użytkownika do ide

- Dodawanie okien narzędzi dla nowych funkcji

- Rozszerzanie funkcji IntelliSense dla danego języka lub dostarczanie technologii IntelliSense dla nowych języków programowania

- Użyj żarówek, aby zapewnić wskazówki i sugestie, które pomagają programistom pisać lepszy kod

- Włączanie obsługi nowego języka

- Dodawanie niestandardowego typu projektu

- Docieranie do milionów programistów za pośrednictwem portalu Visual Studio Marketplace

  Jeśli nigdy wcześniej nie napisano rozszerzenia programu Visual Studio, należy znaleźć więcej informacji na temat tych funkcji i [na temat Rozpoczynanie tworzenia rozszerzeń programu Visual Studio.](../extensibility/starting-to-develop-visual-studio-extensions.md)

## <a name="install-the-visual-studio-sdk"></a>Instalowanie zestawu Visual Studio SDK
 Zestaw SDK programu Visual Studio jest opcjonalną funkcją w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Co nowego w sdk programu Visual Studio 2017
 Visual Studio SDK ma kilka nowych funkcji, takich jak format VSIX v3, jak również zmiany podziału, które mogą wymagać aktualizacji rozszerzenia. Aby uzyskać więcej informacji, zobacz [Co nowego w SDK programu Visual Studio 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Wskazówki dotyczące środowiska użytkownika programu Visual Studio
 Uzyskaj doskonałe wskazówki dotyczące projektowania interfejsu użytkownika dla rozszerzenia w [wskazówki dotyczące środowiska użytkownika](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)programu Visual Studio.

 Możesz również dowiedzieć się, jak sprawić, aby rozszerzenie wyglądało świetnie na urządzeniach o wysokiej rozdzielczości DPI, za pomocą artykułu Problemy z [rozdzielczością DPI adres.](../extensibility/addressing-dpi-issues2.md)

 Skorzystaj z [usługi obrazu i katalogu,](../extensibility/image-service-and-catalog.md) aby uzyskać doskonałe zarządzanie obrazami i obsługę wysokiej rozdzielczości DPI i motywów.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Znajdowanie i instalowanie istniejących rozszerzeń programu Visual Studio
 Rozszerzenia programu Visual Studio można znaleźć w oknie dialogowym **Rozszerzenia i aktualizacje** w menu **Narzędzia.** Aby uzyskać więcej informacji, zobacz [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Rozszerzenia można również znaleźć w portalu [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Odwołanie do sdk programu Visual Studio
 Odwołanie do interfejsu API SDK programu Visual Studio można znaleźć w [programie Visual Studio SDK Reference](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Przykłady zestawów SDK programu Visual Studio
 Przykłady open source rozszerzeń SDK vs można znaleźć w usłudze GitHub w [programie Visual Studio Samples.](https://github.com/Microsoft/VSSDK-Extensibility-Samples) To repozytorium GitHub zawiera przykłady, które ilustrują różne rozszerzalne funkcje w programie Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Inne zasoby SDK programu Visual Studio
 Jeśli masz pytania dotyczące programu VSSDK lub chcesz podzielić się swoimi doświadczeniami z tworzeniem rozszerzeń, możesz użyć [forum rozszerzalności programu Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) lub programu [ExtendVS Gitter Chatroom](https://gitter.im/Microsoft/extendvs).

 Więcej informacji można znaleźć na [blogu VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) i wielu blogach napisanych przez microsoft mvps:

- [Ulubione rozszerzenia programu Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Rozszerzalność programu Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Rozszerzanie programu Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Zobacz też

- [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Jak: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Często zadawane pytania: Konwertowanie dodatków na rozszerzenia VSPackage](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Zarządzanie wieloma wątkami w kodzie zarządzanym](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
- [Dodawanie poleceń do pasków narzędzi](../extensibility/adding-commands-to-toolbars.md)
- [Rozszerzanie i dostosowywanie okien narzędzi](../extensibility/extending-and-customizing-tool-windows.md)
- [Rozszerzenia edytora i usługi językowej](../extensibility/editor-and-language-service-extensions.md)
- [Rozszerzanie projektów](../extensibility/extending-projects.md)
- [Rozszerzanie ustawień i opcji użytkownika](../extensibility/extending-user-settings-and-options.md)
- [Tworzenie niestandardowych szablonów projektów i elementów](../extensibility/creating-custom-project-and-item-templates.md)
- [Rozszerzanie właściwości i okna właściwości](../extensibility/extending-properties-and-the-property-window.md)
- [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Korzystanie i świadczenie usług](../extensibility/using-and-providing-services.md)
- [Zarządzanie pakietami VSPackage](../extensibility/managing-vspackages.md)
- [Izolowana powłoka programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Wysyłaj rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Wewnątrz zestawu Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Obsługa zestawu Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Odwołanie do sdk programu Visual Studio](../extensibility/visual-studio-sdk-reference.md)
