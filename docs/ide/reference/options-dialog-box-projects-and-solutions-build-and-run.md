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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461391"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Okno dialogowe Opcje: \> Tworzenie i uruchamianie projektów i rozwiązań

W tym oknie dialogowym można określić maksymalną liczbę projektów C++ lub C#, które można tworzyć w tym samym czasie, niektóre domyślne zachowania kompilacji i niektóre ustawienia dziennika kompilacji. Aby uzyskać dostęp do tych opcji, wybierz pozycję**Opcje** **narzędzi** > rozwiń pozycję Projekty **i rozwiązania**, a następnie wybierz pozycję **Buduj i uruchamiaj**.

**Maksymalna liczba równoległych kompilacji projektów**

Określa maksymalną liczbę projektów C++ i C#, które można tworzyć w tym samym czasie. Aby zoptymalizować proces kompilacji, maksymalna liczba równoległych kompilacji projektu jest automatycznie ustawiana na liczbę procesorów komputera. Wartość maksymalna to 32.

**Tworzenie tylko projektów uruchamiania i zależności w przebiegu**

Tworzy tylko projekt startowy i jego zależności podczas korzystania z klucza **F5,** **debugowania** > **start** polecenia menu lub odpowiednich poleceń w menu **Kompilacja.** Jeśli nie jest zaznaczone, wszystkie projekty i zależności są budowane.

**W przebiegu, gdy projekty są nieaktualne**

*Dotyczy tylko projektów języka C++.*

Podczas uruchamiania projektu za pomocą **polecenia Debugowanie rozpocznie** **debugowanie lub Debugowanie,** > **Start Debugging** domyślne ustawienie Prompt **do kompilacji** wyświetla komunikat, jeśli konfiguracja projektu jest nieaktualna. Wybierz **opcję Zawsze buduj,** aby utworzyć projekt za każdym razem, gdy jest uruchamiany. Wybierz **opcję Nigdy nie buduj,** aby pominąć wszystkie kompilacje automatyczne po uruchomieniu projektu.

**W przebiegu, gdy występują błędy kompilacji lub wdrożenia**

*Dotyczy tylko projektów języka C++.*

Podczas uruchamiania projektu za pomocą **polecenia Debugowanie** **rozpocznie debugowanie** **debugowania** > domyślne ustawienie **Prompt do uruchomienia** wyświetla komunikat, jeśli projekt powinien zostać uruchomiony, nawet jeśli kompilacja nie powiodła się. Wybierz **uruchom starą wersję,** aby automatycznie uruchomić ostatnią dobrą kompilację, co może spowodować niezgodności między uruchomionym kodem a kodem źródłowym. Wybierz **opcję Nie uruchamiaj,** aby pominąć wiadomość.

**W przypadku nowych rozwiązań użyj aktualnie wybranego projektu jako projektu startowego**

Po ustawieniu tej opcji nowe rozwiązania używają aktualnie wybranego projektu jako projektu startowego.

**Szczegółowość danych wyjściowych kompilacji projektu MSBuild**

Określa, ile informacji z procesu kompilacji jest wyświetlanych w oknie **Dane wyjściowe.**

**Szczegółowość pliku dziennika kompilacji projektu MSBuild**

*Dotyczy tylko projektów języka C++.*

Określa, ile informacji jest zapisywanych w pliku dziennika kompilacji, który znajduje się w * \\ \<pliku ProjectName\\\<>\Debug ProjectName>.log*.

## <a name="see-also"></a>Zobacz też

- [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)
- [Okno dialogowe Opcje, projekty i rozwiązania](projects-and-solutions-options-dialog-box.md)
- [Okno dialogowe Opcje, Projekty i rozwiązania, Projekty internetowe](options-dialog-box-projects-and-solutions-web-projects.md)