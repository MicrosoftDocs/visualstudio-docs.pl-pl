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
ms.openlocfilehash: 3d0f24dc1afa875183f03e15e46cc2331f27cbf0
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647326"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Okno dialogowe Opcje: Projekty i rozwiązania \> kompilowanie i uruchamianie

W tym oknie można określić maksymalną liczbę C++ lub C# projektów, które można tworzyć w tym samym czasie, niektóre domyślne tworzenia zachowań, a niektóre ustawienia dziennika kompilacji. Aby uzyskać dostęp do tych opcji, należy zaznaczyć **narzędzia** > **opcje** rozwiń **projekty i rozwiązania**, a następnie wybierz **kompilowanie i uruchamianie**.

**Maksymalna liczba równoległych projektów kompilacji**

Określa maksymalną liczbę C++ i C# projektów, które można tworzyć w tym samym czasie. Aby zoptymalizować proces kompilacji, maksymalną liczbę równolegle kompilowanych projektów automatycznie jest równa liczbie procesorów na komputerze. Wartość maksymalna to 32.

**Tylko tworzyć projekty startowe i zależności przy uruchomieniu**

Tworzy tylko projekt startowy i jego zależności, gdy używasz **F5** klucza **debugowania** > **Rozpocznij debugowanie** polecenie menu lub odpowiednich poleceń w **kompilacji** menu. Jeśli nie jest zaznaczone, wszystkie projekty i zależności są kompilowane.

**Przy starcie, gdy projekty są nieaktualne**

*Dotyczy tylko projektów w języku C++.*

Podczas uruchamiania projektu za pomocą **F5** lub **debugowania** > **Rozpocznij debugowanie** polecenie domyślne ustawienie **Monituj o kompilacji** Wyświetla komunikat, jeżeli plik konfiguracyjny jest nieaktualna. Wybierz **kompilacji zawsze** do skompilowania projektu, za każdym razem, gdy jest uruchomiony. Wybierz **nigdy nie Kompiluj** pominąć wszystkie kompilacje automatyczne po uruchomieniu projektu.

**Uruchom następujący skrypt, podczas kompilacji lub występują błędy związane z wdrażaniem**

*Dotyczy tylko projektów w języku C++.*

Podczas uruchamiania projektu za pomocą **F5** lub **debugowania** > **Rozpocznij debugowanie** polecenie domyślne ustawienie **Prompt uruchomić**wyświetla komunikat, jeżeli projekt powinien być uruchamiany nawet wtedy, gdy kompilacja nie powiodła się. Wybierz **uruchamiania starej wersji** można automatycznie uruchomić ostatnią dobrą kompilacją, co może spowodować niezgodności między uruchomiony kod i kod źródłowy. Wybierz **nie uruchamiaj** Aby pominąć komunikat.

**W przypadku nowych rozwiązań Użyj obecnie wybranego projektu jako projekt startowy**

Gdy ta opcja jest ustawiona, nowych rozwiązań Użyj obecnie wybranego projektu jako projekt startowy.

**Program MSBuild poziom szczegółowości danych wyjściowych kompilacji dla projektu**

Określa, ile informacji z procesu kompilacji jest wyświetlany w **dane wyjściowe** okna.

**Poziom szczegółowości pliku dziennika MSBuild projektu kompilacji**

*Dotyczy tylko projektów w języku C++.*

Określa, ile informacji ma są zapisywane do pliku dziennika kompilacji, który znajduje się w folderze  *\\ \<nazwa_projektu > \Debug\\\<nazwa_projektu > .log*.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)
- [Okno dialogowe Opcje, projekty i rozwiązania](projects-and-solutions-options-dialog-box.md)
- [Okno dialogowe Opcje, Projekty i rozwiązania, Projekty internetowe](options-dialog-box-projects-and-solutions-web-projects.md)