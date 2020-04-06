---
title: Przygotowywanie rozszerzeń do wdrażania Instalatora Windows | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702031"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Przygotowywanie rozszerzeń do wdrożenia Instalatora Windows
Nie można użyć pakietu Instalatora Windows (MSI) do wdrożenia pakietu VSIX. Można jednak wyodrębnić zawartość pakietu VSIX dla wdrożenia MSI. W tym dokumencie pokazano, jak przygotować projekt, którego domyślnym wyjściem jest pakiet VSIX do włączenia w projekcie Instalatora.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Przygotowywanie projektu rozszerzenia do wdrożenia Instalatora Windows
 Wykonaj te kroki w nowych projektach rozszerzenia przed dodaniem do projektu Instalatora.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Aby przygotować projekt rozszerzenia do wdrożenia Instalatora Windows

1. Utwórz VSPackage, SKŁADNIK MEF, Edytor Adornment lub inny typ projektu rozszerzalności, który zawiera manifest VSIX.

2. Otwórz manifest VSIX w edytorze kodu.

3. Ustaw `InstalledByMsi` element manifestu VSIX `true`na . Aby uzyskać więcej informacji na temat manifestu VSIX, zobacz [odwołanie do schematu rozszerzenia VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Zapobiega to instalatorowi VSIX próby zainstalowania składnika.

4. Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i kliknij polecenie **Właściwości**.

5. Wybierz kartę **VSIX.**

6. Zaznacz pole wyboru Z etykietą **Kopiuj zawartość VSIX w następującej lokalizacji** i wpisz ścieżkę do miejsca, w którym projekt Instalatora odbierze pliki.

## <a name="extract-files-from-an-existing-vsix-package"></a>Wyodrębnianie plików z istniejącego pakietu VSIX
 Wykonaj następujące kroki, aby dodać zawartość istniejącego pakietu VSIX do projektu Instalatora, gdy nie masz plików źródłowych.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Aby wyodrębnić pliki z istniejącego pakietu VSIX

1. Zmień nazwę pliku *. VSIX* zawierający rozszerzenie od *filename.vsix* do *filename.zip*.

2. Skopiuj zawartość pliku *zip* do katalogu.

3. Usuń *plik [Content_types].xml* z katalogu.

4. Edytuj manifest VSIX, jak pokazano w poprzedniej procedurze.

5. Dodaj pozostałe pliki do projektu instalatora.

## <a name="see-also"></a>Zobacz też
- [Wdrażanie instalatora programu Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Instruktaż: Tworzenie akcji niestandardowej](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
