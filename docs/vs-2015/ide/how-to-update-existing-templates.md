---
title: 'Instrukcje: aktualizowanie istniejących szablonów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b56cf11057957b0eb99fc065ed26af10d8adfbd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670587"
---
# <a name="how-to-update-existing-templates"></a>Porady: aktualizowanie istniejących szablonów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po utworzeniu szablonu i przeprowadzeniu kompresji plików do pliku zip warto zmodyfikować szablon. Można to zrobić przez ręczne zmianę plików w szablonie lub przez wyeksportowanie nowego szablonu z projektu opartego na szablonie.

## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Aktualizowanie istniejącego szablonu za pomocą Kreatora eksportu szablonów
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] udostępnia kreatora **eksportu szablonu** , którego można użyć do zaktualizowania istniejącego szablonu.

#### <a name="to-use-export-template-to-update-an-existing-template"></a>Aby zaktualizować istniejący szablon przy użyciu szablonu eksportu

1. W menu **plik** kliknij pozycję **Nowy** , a następnie kliknij pozycję **Nowy projekt**.

2. Wybierz szablon, który chcesz zaktualizować, wprowadź nazwę i lokalizację projektu tymczasowego, a następnie kliknij przycisk **OK**.

3. Zmodyfikuj projekt w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. W menu **plik** kliknij polecenie **Eksportuj szablon**i użyj kreatora **eksportu szablonów** , aby utworzyć nowy szablon.

5. Po skompresowaniu zaktualizowanego szablonu do pliku zip Usuń stary plik Template. zip.

## <a name="manually-updating-an-existing-template"></a>Ręczne aktualizowanie istniejącego szablonu
 Istniejący szablon można zaktualizować poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], modyfikując pliki w skompresowanym pliku zip.

#### <a name="to-manually-update-an-existing-template"></a>Aby ręcznie zaktualizować istniejący szablon

1. Znajdź plik zip, który zawiera szablon. Domyślnie ten plik znajduje się w pliku \Moje Documents\Visual Studio w *wersji*\Moje wyeksportowane szablony \\.

2. Wyodrębnij plik zip.

3. Zmodyfikuj lub Usuń bieżące pliki szablonu lub Dodaj nowe pliki do szablonu.

4. Otwórz, zmodyfikuj i Zapisz plik XML. vstemplate, aby obsłużyć zaktualizowane zachowanie lub nowe pliki. Aby uzyskać więcej informacji o schemacie. vstemplate, zobacz [Dokumentacja schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Aby uzyskać więcej informacji o tym, co można Sparametryzuj w plikach źródłowych, zobacz [Parametry szablonu](../ide/template-parameters.md)

5. Wybierz pliki w szablonie, kliknij prawym przyciskiem myszy, kliknij polecenie **Wyślij do**, a następnie kliknij **folder skompresowany (zip)** . Wybrane pliki są kompresowane do pliku zip.

6. Umieść nowy plik zip w tym samym katalogu, w którym znajduje się stary plik. zip.

7. Usuń wyodrębnione pliki szablonów i stary plik Template. zip.

8. Uruchom (jako administrator) wystąpienie wiersz polecenia dla deweloperów (w menu Start w obszarze **Visual Studio 2010/Visual Studio Tools/wiersz polecenia dla deweloperów**).

9. Uruchom następujące polecenie: `devenv /installvstemplates`.

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md) [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md) szablon [programu Visual Studio szablonu odwołania](../extensibility/visual-studio-template-schema-reference.md) [Parametry szablonu](../ide/template-parameters.md) [, instrukcje: Tworzenie zestawów początkowych](../ide/how-to-create-starter-kits.md)
