---
title: Wysyłka rozszerzeń programu Visual Studio | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700112"
---
# <a name="shipping-visual-studio-extensions"></a>Dostarczanie rozszerzeń programu Visual Studio
Po zakończeniu tworzenia rozszerzenia można zainstalować je na innych komputerach, udostępnić go znajomym i współpracownikom lub opublikować go w witrynie Visual Studio Marketplace. W tej sekcji wyjaśniamy wszystkie czynności, które należy zrobić, aby opublikować i zachować rozszerzenie: pracę z plikami .vsix, publikowanie, lokalizowanie i aktualizowanie.

## <a name="working-with-vsix-extensions"></a>Praca z rozszerzeniami VSIX
 Rozszerzenia VSIX można utworzyć, tworząc pusty projekt VSIX, a następnie dodając do niego różne szablony elementów. Aby uzyskać więcej informacji, zobacz [Szablon projektu VSIX](../extensibility/vsix-project-template.md).

 Za pomocą formatu VSIX można spakować szablony projektów, szablony elementów, pakiety VSPackages, składniki mef (Managed Extensibility Framework), formanty **przybornika,** zestawy i typy niestandardowe (obejmuje to niestandardowe strony startowe dla programu Visual Studio 2017). Format VSIX używa wdrożenia opartego na plikach. Aby uzyskać więcej informacji na temat pakietów VSIX, zobacz [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Format VSIX nie obsługuje instalacji fragmentów kodu. Nie obsługuje również niektórych innych scenariuszy, takich jak zapisywanie do globalnej pamięci podręcznej zestawów (GAC) lub do rejestru systemu. Jeśli chcesz napisać do gac lub rejestru w instalacji, należy użyć Instalatora Windows. Aby uzyskać więcej informacji, zobacz [Przygotowywanie rozszerzeń dla wdrażania Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publikowanie rozszerzenia w witrynie Visual Studio Marketplace
 Rozszerzenie można rozpowszechniać wśród innych osób, wysyłając im plik .vsix lub wstawiając je na serwer. Ale najlepszym sposobem, aby uzyskać kod w rękach wielu ludzi jest umieszczenie go na [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Rozszerzenia programu Visual Studio Marketplace są dostępne dla użytkowników programu Visual Studio za pośrednictwem **rozszerzeń i aktualizacji.** Aby uzyskać więcej informacji, zobacz [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Pełny przykład, który pokazuje, jak przekazać rozszerzenie do portalu Visual Studio Marketplace, zobacz [Instruktaż: Publikowanie rozszerzenia programu Visual Studio.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)

## <a name="private-galleries"></a>Galerie prywatne
 Podczas opracowywania formantów, szablonów i narzędzi można je udostępniać organizacji, publikując je w prywatnej galerii w intranecie. Aby uzyskać więcej informacji, zobacz [Galerie prywatne](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Lokalizowanie rozszerzenia
 Jeśli planujesz zwolnić rozszerzenie w różnych lokalizacjach, należy rozważyć jego zlokalizowanie. Aby uzyskać wyjaśnienie, o co chodzi, zobacz [Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aktualizowanie i przechowywanie wersji rozszerzenia
 Po opublikowaniu rozszerzenia nadejdzie czas, kiedy trzeba je zaktualizować. Aby dowiedzieć się, jak zaktualizować rozszerzenie opublikowane w portalu Visual Studio Marketplace, zobacz [Jak: Aktualizowanie rozszerzenia](../extensibility/how-to-update-a-visual-studio-extension.md).

 Rozszerzenie można ustawić tak, aby obsługiwało wiele wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Obsługa wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|W tym artykule wyjaśniono, jak zainstalować szablon projektu niestandardowego za pomocą szablonu projektu VSIX.|
|[Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Opisuje składniki pakietu VSIX.|
|[Szablon projektu VSIX](../extensibility/vsix-project-template.md)|Zawiera instrukcje krok po kroku dotyczące sposobu pakowania i publikowania rozszerzenia.|
|[Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)|W tym artykule wyjaśniono, jak dostarczyć zlokalizowany tekst dla procesu instalacji przy użyciu plików extension.vsixlangpack.|
|[Instrukcje: aktualizowanie rozszerzenia](../extensibility/how-to-update-a-visual-studio-extension.md)|W tym artykule opisano, jak zaktualizować rozszerzenie w systemie i jak wdrożyć aktualizację do istniejącego rozszerzenia programu Visual Studio.|
|[Instrukcje: dodawanie zależności do pakietu VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|W tym artykule opisano sposób dodawania odwołań do pakietów wdrażania vsix.|
|[Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|W tym artykule wyjaśniono, jak wdrożyć rozszerzenie za pomocą Instalatora Windows.|
|[Podpisywanie pakietów VSIX](../extensibility/signing-vsix-packages.md)|W tym artykule wyjaśniono, jak podpisać pakiety VSIX.|
|[Galerie prywatne](../extensibility/private-galleries.md)|W tym artykule wyjaśniono, jak tworzyć prywatne galerie dla rozszerzeń.|
|[Obsługiwanie wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Pokazuje, jak mieć rozszerzenie obsługuje wiele wersji programu Visual Studio.|
|[Lokalizowanie z programu Visual Studio](locating-visual-studio.md)|W tym artykule opisano sposób lokalizowania wystąpień programu Visual Studio dla wdrożenia rozszerzenia niestandardowego.|
