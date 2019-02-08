---
title: Okno dialogowe Opcje, Projekty i rozwiązania, Kompilowanie i uruchamianie
ms.date: 07/14/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e2e62a0b9ece6052d222a8c228bbd7fe018b0a3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954780"
---
# <a name="options-dialog-box-projects-and-solutions-build-and-run"></a>Okno dialogowe Opcje, Projekty i rozwiązania, Kompilowanie i uruchamianie

W tym oknie można określić maksymalną liczbę Visual C++ lub C# projektów, które można tworzyć w tym samym czasie, niektóre domyślne tworzenia zachowań, a niektóre ustawienia dziennika kompilacji. Aby uzyskać dostęp do tych opcji, należy zaznaczyć **Narzędzia > Opcje** rozwiń **projekty i rozwiązania**i wybierz pozycję **kompilowanie i uruchamianie**.

**Maksymalna liczba równoległych projektów kompilacji**

Określa maksymalną liczbę Visual C++ i C# projektów, które można tworzyć w tym samym czasie. Aby zoptymalizować proces kompilacji, maksymalną liczbę równolegle kompilowanych projektów automatycznie jest równa liczbie procesorów na komputerze. Wartość maksymalna to 32.

**Tylko tworzyć projekty startowe i zależności przy uruchomieniu**

Kompiluje tylko projekt startowy i jego zależności, korzystając z klucza, wybierz opcję F5 **Debuguj > Rozpocznij** polecenie menu lub odpowiednich poleceń w **kompilacji** menu. Jeśli jest to jasne, wszystkie projekty i zależności są kompilowane.

**Przy starcie, gdy projekty są nieaktualne**

*Dotyczy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] wyłącznie dla projektów.*

Podczas uruchamiania projektu, naciskając klawisz F5 lub **Debuguj > Start** polecenie domyślne ustawienie **Monituj o kompilacji** wyświetla komunikat, jeżeli plik konfiguracyjny jest nieaktualna. Wybierz **kompilacji zawsze** do skompilowania projektu, za każdym razem, gdy jest uruchomiony. Wybierz **nigdy nie Kompiluj** pominąć wszystkie kompilacje automatyczne po uruchomieniu projektu.

**Uruchom następujący skrypt, podczas kompilacji lub występują błędy związane z wdrażaniem**

*Dotyczy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] wyłącznie dla projektów.*

Podczas uruchamiania projektu, naciskając klawisz F5 lub **Debuguj > Uruchom** polecenie domyślne ustawienie **Prompt uruchomić** wyświetla komunikat, jeżeli projekt powinien być uruchamiany nawet wtedy, gdy kompilacja nie powiodła się. Wybierz **uruchamiania starej wersji** można automatycznie uruchomić ostatnią dobrą kompilacją, co może spowodować niezgodności między uruchomiony kod i kod źródłowy. Wybierz **nie uruchamiaj** Aby pominąć komunikat.

**W przypadku nowych rozwiązań Użyj obecnie wybranego projektu jako projekt startowy**

Gdy ta opcja jest ustawiona, nowych rozwiązań Użyj obecnie wybranego projektu jako projekt startowy.

**Program MSBuild poziom szczegółowości danych wyjściowych kompilacji dla projektu**

Określa, ile informacji ma pojawia się w **dane wyjściowe** okna dla kompilacji.

**Poziom szczegółowości pliku dziennika MSBuild projektu kompilacji**

*Dotyczy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] wyłącznie dla projektów.*

Określa, ile informacji ma są zapisywane do pliku dziennika kompilacji, który znajduje się w folderze \\... \\ *ProjectName*\Debug\\*ProjectName*. log.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)
- [Okno dialogowe Opcje, projekty i rozwiązania](projects-and-solutions-options-dialog-box.md)
- [Okno dialogowe Opcje, Projekty i rozwiązania, Projekty internetowe](options-dialog-box-projects-and-solutions-web-projects.md)