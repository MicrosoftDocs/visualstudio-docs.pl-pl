---
title: Wysyłanie rozszerzenia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ed8080b8e470276a38fbf300edbf801dc8e141fd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785267"
---
# <a name="shipping-visual-studio-extensions"></a>Dostarczanie rozszerzeń programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Uwaga**: W galerii Visual Studio jest zastępowany przez Visual Studio Marketplace. Zobaczyć najnowszą wersję tego tematu, aby uzyskać szczegółowe informacje.


Po zakończeniu tworzenia Twojego rozszerzenia, możesz zainstalować ją na innych komputerach, udostępnić go ze znajomymi współpracowników lub opublikować ją w galerii Visual Studio. W tej sekcji Wyjaśnijmy, wszystkie elementy, które należy wykonać w celu publikowania i obsługa rozszerzenia: Praca z plikami .vsix, publikowania, lokalizacja i aktualizowania.

## <a name="working-with-vsix-extensions"></a>Praca z rozszerzeniami VSIX
 Tworzenie pustego projektu VSIX, a następnie dodając szablony różnych elementów do niego, można utworzyć rozszerzenia VSIX. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).

 Można użyć formatu VSIX pakietu szablony projektów, szablonów, pakietów VSPackage, składniki Managed Extensibility Framework (MEF), element **przybornika** formantów, zestawów i typów niestandardowych (w tym niestandardowych stron Start). VSIX format używa wdrożenia oparte na plikach. Aby uzyskać więcej informacji na temat pakietów VSIX, zobacz [anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 VSIX format nie obsługuje instalacji fragmentów kodu. Nie obsługuje ona również niektórych innych scenariuszach, takich jak zapisywanie do globalnej pamięci podręcznej zestawów (GAC) lub w rejestrze systemu. Jeśli trzeba zapisać w pamięci podręcznej GAC i rejestru w instalacji, należy użyć Instalatora Windows. Aby uzyskać więcej informacji, zobacz [przygotowywanie rozszerzeń dla Windows wdrażanie za pomocą Instalatora](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-gallery"></a>Publikowanie rozszerzenia do galerii Visual Studio
 Można rozpowszechniać swoje rozszerzenia innym osobom poprzez zamieszkania ich plik .vsix lub umieszczenie w na serwerze. Ale najlepszy sposób pozyskania swój kod w ręce wiele osób, umieść je w [galerii Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847). Rozszerzenia z galerii programu Visual Studio są dostępne dla użytkowników programu Visual Studio za pośrednictwem **rozszerzenia i aktualizacje**. Aby uzyskać więcej informacji, zobacz [Znajdowanie i przy użyciu rozszerzenia programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Aby uzyskać pełny przykład, który pokazuje, jak przekazać rozszerzenie do galerii Visual Studio, zobacz [instruktażu: Publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Galerie prywatne
 Podczas opracowywania formanty, szablony i narzędzia, można udostępnianie w organizacji, publikując je ona prywatną galerię w sieci intranet. Aby uzyskać więcej informacji, zobacz [galerie prywatne](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Lokalizowanie rozszerzenia
 Jeśli planowane jest wersji Twojego rozszerzenia w różnych ustawień regionalnych, należy rozważyć lokalizowania go. Opis na czym polega znaleźć [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aktualizowanie i przechowywanie wersji rozszerzenia
 Po opublikowaniu Twojego rozszerzenia, będzie dostępna przez czas, kiedy trzeba będzie ją zaktualizować. Aby dowiedzieć się, jak zaktualizować rozszerzenia, które zostały opublikowane w galerii Visual Studio, zobacz [jak: Aktualizuj rozszerzenie](../extensibility/how-to-update-a-visual-studio-extension.md).

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
