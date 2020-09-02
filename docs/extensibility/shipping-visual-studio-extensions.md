---
title: Wysyłanie rozszerzeń programu Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700112"
---
# <a name="shipping-visual-studio-extensions"></a>Dostarczanie rozszerzeń programu Visual Studio
Po zakończeniu opracowywania rozszerzenia można go zainstalować na innych maszynach, udostępnić go znajomym i współpracownikom albo opublikować na Visual Studio Marketplace. W tej sekcji wyjaśnimy wszystkie czynności, które należy wykonać w celu opublikowania i utrzymania rozszerzenia: Praca z plikami. vsix, publikowanie, lokalizowanie i aktualizowanie.

## <a name="working-with-vsix-extensions"></a>Praca z rozszerzeniami VSIX
 Rozszerzenia VSIX można utworzyć, tworząc pusty projekt VSIX, a następnie dodając do niego różne szablony elementów. Aby uzyskać więcej informacji, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

 Można użyć formatu VSIX do spakowania szablonów projektu, szablonów elementów, pakietów VSPackage, składników Managed Extensibility Framework (MEF), formantów **przybornika** , zestawów i typów niestandardowych (obejmuje to niestandardowe strony początkowe dla programu Visual Studio 2017). Format VSIX używa wdrożenia opartego na plikach. Aby uzyskać więcej informacji na temat pakietów VSIX, zobacz [anatomię pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Format VSIX nie obsługuje instalacji fragmentów kodu. Nie obsługuje również niektórych innych scenariuszy, takich jak zapisywanie do globalnej pamięci podręcznej zestawów (GAC) lub rejestr systemowy. Jeśli konieczne jest zapisanie w pamięci GAC lub w rejestrze w instalacji, należy użyć Instalator Windows. Aby uzyskać więcej informacji, zobacz [Przygotowywanie rozszerzeń wdrożenia Instalator Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publikowanie rozszerzenia w Visual Studio Marketplace
 Rozszerzenie można rozpowszechnić na inne osoby, wysyłając je do pliku. vsix lub umieszczając na serwerze. Jednak najlepszym sposobem na uzyskanie kodu w ręce wielu osób jest umieszczenie go w [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Rozszerzenia Visual Studio Marketplace są dostępne dla użytkowników programu Visual Studio przez **rozszerzenia i aktualizacje**. Aby uzyskać więcej informacji, zobacz [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Pełny przykład przedstawiający sposób przekazywania rozszerzenia do Visual Studio Marketplace można znaleźć w [przewodniku: Publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Galerie prywatne
 Podczas tworzenia formantów, szablonów i narzędzi można udostępniać je organizacji, publikując je w prywatnej galerii w intranecie. Aby uzyskać więcej informacji, zobacz [prywatne galerie](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Lokalizowanie rozszerzenia
 Jeśli planujesz wydanie rozszerzenia w różnych ustawieniach regionalnych, należy rozważyć jego lokalizowanie. Aby zapoznać się z informacjami dotyczącymi tego, czego dotyczy, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aktualizowanie i przechowywanie wersji rozszerzenia
 Po opublikowaniu rozszerzenia pozostanie czas, gdy trzeba go zaktualizować. Aby dowiedzieć się, jak zaktualizować rozszerzenie opublikowane na Visual Studio Marketplace, zobacz [How to: Update a Extension](../extensibility/how-to-update-a-visual-studio-extension.md).

 Możesz ustawić rozszerzenie, aby obsługiwało wiele wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Obsługa wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Wyjaśnia, w jaki sposób używać szablonu projektu VSIX do instalowania niestandardowego szablonu projektu.|
|[Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Opisuje składniki pakietu VSIX.|
|[Szablon projektu VSIX](../extensibility/vsix-project-template.md)|Zawiera instrukcje krok po kroku dotyczące sposobu pakowania i publikowania rozszerzenia.|
|[Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)|Wyjaśnia, jak zapewnić zlokalizowany tekst dla procesu instalacji przy użyciu plików rozszerzenia. vsixlangpack.|
|[Instrukcje: aktualizowanie rozszerzenia](../extensibility/how-to-update-a-visual-studio-extension.md)|Opisuje sposób aktualizowania rozszerzenia w systemie i wdrażania aktualizacji w istniejącym rozszerzeniu programu Visual Studio.|
|[Instrukcje: dodawanie zależności do pakietu VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Opisuje sposób dodawania odwołań do pakietów wdrożeniowych VSIX.|
|[Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Wyjaśnia, jak wdrożyć rozszerzenie za pomocą Instalator Windows.|
|[Podpisywanie pakietów VSIX](../extensibility/signing-vsix-packages.md)|Wyjaśnia, jak podpisać pakiety VSIX.|
|[Galerie prywatne](../extensibility/private-galleries.md)|Wyjaśnia, jak utworzyć Galerie prywatne dla rozszerzeń.|
|[Obsługiwanie wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Pokazuje, w jaki sposób rozszerzenie ma obsługiwać wiele wersji programu Visual Studio.|
|[Lokalizowanie z programu Visual Studio](locating-visual-studio.md)|Opisuje sposób lokalizowania wystąpień programu Visual Studio na potrzeby wdrożenia rozszerzeń niestandardowych.|
