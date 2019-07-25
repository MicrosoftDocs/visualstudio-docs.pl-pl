---
title: Okno dialogowe Opcje, Projekty i rozwiązania, Kompilowanie i uruchamianie
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24ba5bbf34ecc12c2508c538e74909ee0a10aef4
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461391"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Opcje — okno dialogowe: Kompilowanie i \> uruchamianie projektów i rozwiązań

W tym oknie dialogowym można określić maksymalną liczbę C++ lub C# projekty, które mogą być kompilowane w tym samym czasie, niektóre domyślne zachowania kompilacji i niektóre ustawienia dziennika kompilacji. Aby uzyskać dostęp do tych opcji, wybierz**Opcje** **Narzędzia** > rozwiń węzeł **projekty i rozwiązania**, a następnie wybierz opcję **Kompiluj i uruchom**.

**Maksymalna liczba równoległych kompilacji projektów**

Określa maksymalną liczbę C++ i C# projekty, które mogą być kompilowane w tym samym czasie. Aby zoptymalizować proces kompilacji, Maksymalna liczba kompilacji projektów równoległych jest automatycznie ustawiana na liczbę procesorów danego komputera. Wartość maksymalna to 32.

**Kompiluj tylko projekty startowe i zależności przy uruchomieniu**

Kompiluje tylko projekt startowy i jego zależności przy użyciu klawisza **F5** , polecenia **debugowania** > **Rozpocznij debugowanie** lub odpowiednich poleceń w menu **kompilacja** . W przypadku usunięcia zaznaczenia wszystkie projekty i zależności są kompilowane.

**Przy uruchomieniu, gdy projekty są nieaktualne**

*Dotyczy tylko C++ projektów.*

W przypadku uruchamiania projektu z poleceniem **F5** lub **Debuguj** > **Rozpocznij debugowanie** , w **wierszu** ustawienia domyślnego zostanie wyświetlony komunikat o błędzie, jeśli konfiguracja projektu jest nieaktualna. Wybierz pozycję **zawsze Kompiluj** , aby skompilować projekt przy każdym uruchomieniu. Wybierz pozycję **nigdy Kompiluj** , aby pominąć wszystkie kompilacje automatyczne, gdy projekt jest uruchomiony.

**Przy uruchomieniu, gdy wystąpią błędy kompilacji lub wdrożenia**

*Dotyczy tylko C++ projektów.*

Podczas uruchamiania projektu z poleceniem **F5** lub **Debuguj** > **Rozpocznij debugowanie** , **monit** ustawienia domyślnego o uruchomienie wyświetla komunikat, jeśli projekt powinien zostać uruchomiony, nawet jeśli kompilacja nie powiodła się. Wybierz pozycję **Uruchom starą wersję** , aby automatycznie uruchomić ostatnią dobrą kompilację, co może spowodować niezgodność między uruchomionym kodem a kodem źródłowym. Wybierz  pozycję nie uruchamiaj, aby pominąć komunikat.

**W przypadku nowych rozwiązań Użyj obecnie wybranego projektu jako projektu startowego**

Gdy ta opcja jest ustawiona, nowe rozwiązania używają aktualnie wybranego projektu jako projektu startowego.

**Poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild**

Określa, ile informacji z procesu kompilacji jest wyświetlanych w oknie **danych wyjściowych** .

**Poziom szczegółowości pliku dziennika kompilacji projektu programu MSBuild**

*Dotyczy tylko C++ projektów.*

Określa, ile informacji jest zapisywana w pliku dziennika kompilacji, który znajduje się w  *\\ \<ProjectName > \debug.\\\<ProjectName >. log*.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)
- [Okno dialogowe Opcje, projekty i rozwiązania](projects-and-solutions-options-dialog-box.md)
- [Okno dialogowe Opcje, Projekty i rozwiązania, Projekty internetowe](options-dialog-box-projects-and-solutions-web-projects.md)