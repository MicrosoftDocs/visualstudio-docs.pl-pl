---
title: Przygotowywanie rozszerzeń wdrożenia Instalator Windows | Microsoft Docs
description: Dowiedz się, jak przygotować projekt, którego domyślne dane wyjściowe są pakietem VSIX do uwzględnienia w projekcie instalacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6436d05d3b15be1c1fe8d7c7bb9c8592dee091dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090281"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Przygotuj rozszerzenia dla wdrożenia Instalator Windows
Nie można użyć pakietu Instalator Windows (MSI) do wdrożenia pakietu VSIX. Można jednak wyodrębnić zawartość pakietu VSIX dla wdrożenia MSI. W tym dokumencie przedstawiono sposób przygotowania projektu, którego domyślne dane wyjściowe są pakietem VSIX do uwzględnienia w projekcie instalacji.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Przygotuj projekt rozszerzenia dla wdrożenia Instalator Windows
 Wykonaj te kroki w nowych projektach rozszerzeń przed dodaniem do projektu instalacji.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Aby przygotować projekt rozszerzenia dla wdrożenia Instalator Windows

1. Utwórz składnik pakietu VSPackage, MEF, Edytor definiowania układu lub inny typ projektu rozszerzalności, który zawiera manifest VSIX.

2. Otwórz manifest VSIX w edytorze kodu.

3. Ustaw `InstalledByMsi` element manifestu VSIX na `true` . Aby uzyskać więcej informacji na temat manifestu VSIX, zobacz [odwołanie do schematu rozszerzenia vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Zapobiega to próbie zainstalowania składnika przez Instalatora VSIX.

4. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie kliknij pozycję **Właściwości**.

5. Wybierz kartę **VSIX** .

6. Zaznacz pole wyboru **Kopiuj zawartość VSIX do następującej lokalizacji** i wpisz ścieżkę do lokalizacji, w której projekt instalacyjny będzie pobierał pliki.

## <a name="extract-files-from-an-existing-vsix-package"></a>Wyodrębnij pliki z istniejącego pakietu VSIX
 Wykonaj następujące kroki, aby dodać zawartość istniejącego pakietu VSIX do projektu konfiguracji, gdy nie masz plików źródłowych.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Aby wyodrębnić pliki z istniejącego pakietu VSIX

1. Zmień nazwę *. Plik VSIX* zawierający rozszerzenie z *pliku filename. vsix* do *filename.zip*.

2. Skopiuj zawartość pliku *zip* do katalogu.

3. Usuń plik *[Content_Types]. XML* z katalogu.

4. Edytuj manifest VSIX, jak pokazano w poprzedniej procedurze.

5. Dodaj pozostałe pliki do projektu Instalatora.

## <a name="see-also"></a>Zobacz też
- [Wdrożenie Instalatora programu Visual Studio](/previous-versions/2kt85ked(v=vs.120))
- [Przewodnik: Tworzenie akcji niestandardowej](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))