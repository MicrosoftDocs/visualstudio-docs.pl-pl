---
title: Wysyłanie rozszerzeń programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ea2217614ed27a98281cce7a3d34b72f74ae803
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796598"
---
# <a name="shipping-visual-studio-extensions"></a>Dostarczanie rozszerzeń programu Visual Studio
Po zakończeniu tworzenia Twojego rozszerzenia, możesz zainstalować ją na innych komputerach, udostępnić go ze znajomymi współpracowników lub opublikować ją w Visual Studio Marketplace. W tej sekcji Wyjaśnijmy, wszystkie elementy, które należy wykonać w celu publikowania i obsługa rozszerzenia: Praca z plikami .vsix, publikowania, lokalizacja i aktualizowania.

## <a name="working-with-vsix-extensions"></a>Praca z rozszerzeniami VSIX
 Tworzenie pustego projektu VSIX, a następnie dodając szablony różnych elementów do niego, można utworzyć rozszerzenia VSIX. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).

 Można użyć formatu VSIX pakietu szablony projektów, szablonów, pakietów VSPackage, składniki Managed Extensibility Framework (MEF), element **przybornika** formantów, zestawów i typów niestandardowych (dotyczy to Start stron niestandardowych wizualizacji Studio 2017). VSIX format używa wdrożenia oparte na plikach. Aby uzyskać więcej informacji na temat pakietów VSIX, zobacz [anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 VSIX format nie obsługuje instalacji fragmentów kodu. Nie obsługuje ona również niektórych innych scenariuszach, takich jak zapisywanie do globalnej pamięci podręcznej zestawów (GAC) lub w rejestrze systemu. Jeśli trzeba zapisać w pamięci podręcznej GAC i rejestru w instalacji, należy użyć Instalatora Windows. Aby uzyskać więcej informacji, zobacz [przygotowywanie rozszerzeń dla Windows wdrażanie za pomocą Instalatora](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publikowanie rozszerzenia witryny Marketplace programu Visual Studio
 Można rozpowszechniać swoje rozszerzenia innym osobom poprzez zamieszkania ich plik .vsix lub umieszczenie w na serwerze. Ale najlepszy sposób pozyskania swój kod w ręce wiele osób, umieść je w [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Rozszerzenia programu Visual Studio Marketplace są dostępne dla użytkowników programu Visual Studio za pośrednictwem **rozszerzenia i aktualizacje**. Aby uzyskać więcej informacji, zobacz [Znajdowanie i przy użyciu rozszerzenia programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Aby uzyskać pełny przykład, który pokazuje, jak przekazać rozszerzenie do witryny Marketplace programu Visual Studio, zobacz [instruktażu: Publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Galerie prywatne
 Podczas opracowywania formanty, szablony i narzędzia, można udostępnianie w organizacji, publikując je ona prywatną galerię w sieci intranet. Aby uzyskać więcej informacji, zobacz [galerie prywatne](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Lokalizowanie rozszerzenia
 Jeśli planowane jest wersji Twojego rozszerzenia w różnych ustawień regionalnych, należy rozważyć lokalizowania go. Opis na czym polega znaleźć [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aktualizowanie i przechowywanie wersji rozszerzenia
 Po opublikowaniu Twojego rozszerzenia, będzie dostępna przez czas, kiedy trzeba będzie ją zaktualizować. Aby dowiedzieć się, jak można zaktualizować rozszerzenia, które zostały opublikowane w witrynie Visual Studio Marketplace, zobacz [jak: Aktualizuj rozszerzenie](../extensibility/how-to-update-a-visual-studio-extension.md).

 Można ustawić rozszerzenie obsługi wielu wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [obsługi wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Wyjaśnia, jak użyć szablonu projektu VSIX do zainstalowania szablonu niestandardowego projektu.|
|[Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)|W tym artykule opisano składniki pakietu VSIX.|
|[Szablon projektu VSIX](../extensibility/vsix-project-template.md)|Instrukcje krok po kroku o pakietach i publikowanie rozszerzenia.|
|[Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)|Wyjaśnia sposób zapewnienia zlokalizowanego tekstu w trakcie instalacji przy użyciu extension.vsixlangpack plików.|
|[Instrukcje: Aktualizuj rozszerzenie](../extensibility/how-to-update-a-visual-studio-extension.md)|Opisuje sposób aktualizacji rozszerzenia w systemie oraz wdrożenia aktualizacji na istniejące rozszerzenie programu Visual Studio.|
|[Instrukcje: Dodawanie zależności do pakietu VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|W tym artykule opisano, jak dodać odwołania do pakietów wdrożeniowych VSIX.|
|[Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Wyjaśnia sposób wdrażania rozszerzenia za pomocą Instalatora Windows.|
|[Podpisywanie pakietów VSIX](../extensibility/signing-vsix-packages.md)|Opisuje sposób rejestrowania pakietów VSIX.|
|[Galerie prywatne](../extensibility/private-galleries.md)|Wyjaśnia sposób tworzenia prywatnych galerii rozszerzeń.|
|[Obsługiwanie wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Pokazuje, jak obsługują rozszerzenia wielu wersji programu Visual Studio.|
|[Lokalizowanie z programu Visual Studio](locating-visual-studio.md)|Opisuje sposób znaleźć wystąpień programu Visual Studio do wdrażania niestandardowego rozszerzenia.|
