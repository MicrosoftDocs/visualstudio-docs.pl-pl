---
title: Debuguj aplikację, która nie jest częścią rozwiązania programu Visual Studio
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 740af718a2928991d46bedbd6709337b9b20a254
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557911"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Debuguj aplikację, która nie jest częścią rozwiązania programu Visual Studio (C++, C#, Visual Basic F#)

Możesz chcieć debugować aplikację (plik*exe* ), która nie jest częścią rozwiązania programu Visual Studio. Może to być [otwarty projekt folderu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) lub ktoś inny mógł utworzyć aplikację poza programem Visual Studio lub uzyskać aplikację z innej lokalizacji.

- W przypadku projektu otwartego folderu w programie Visual Studio (który nie ma pliku projektu lub rozwiązania), zobacz [Uruchamianie i debugowanie kodu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) lub, C++w przypadku, [Konfigurowanie parametrów debugowania za pomocą pliku Launch. vs. JSON](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- W przypadku aplikacji, która nie istnieje w programie Visual Studio, typowym sposobem debugowania jest uruchomienie aplikacji poza programem Visual Studio, a następnie dołączenie do niej przy użyciu opcji **Dołącz do procesu** w debugerze programu Visual Studio. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Dołączanie do aplikacji wymaga ręczne wykonanie czynności, które po kilku sekundach. Ze względu na to opóźnienie dołączanie nie pomoże, debugować problem uruchamiania lub aplikację, która nie czeka na użytkownika, danych wejściowych i szybko się kończy.

   W takich przypadkach można utworzyć projekt EXE usługi Visual Studio dla aplikacji lub zaimportować go do istniejącego C#, Visual Basic lub C++ rozwiązania. Nie wszystkie języki programowania wspierają projekty EXE.

>[!IMPORTANT]
>Funkcje debugowania dla aplikacji, która nie została utworzona w programie Visual Studio są ograniczone, czy dołączyć do aplikacji, albo dodaj go do rozwiązania programu Visual Studio.
>
>Jeśli masz kod źródłowy, najlepszym rozwiązaniem jest importowanie kodu do projektu programu Visual Studio. Następnie uruchom kompilację debugowania aplikacji.
>
>Jeśli nie masz kodu źródłowego, a aplikacja nie ma [informacji debugowania](../debugger/how-to-set-debug-and-release-configurations.md) w zgodnym formacie, dostępne funkcje debugowania są bardzo mało.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Aby utworzyć nowy projekt EXE dla istniejącej aplikacji

1. W programie Visual Studio wybierz pozycję **plik** > **Otwórz** > **Project**.

1. W oknie dialogowym **Otwórz projekt** zaznacz opcję **wszystkie pliki projektu**, jeśli nie została jeszcze wybrana, na liście rozwijanej obok pola **Nazwa pliku**.

1. Przejdź do pliku *. exe* , zaznacz go, a następnie wybierz pozycję **Otwórz**.

   Plik pojawi się w rozwiązaniu programu Visual Studio do nowego, tymczasowego.

1. Rozpocznij debugowanie aplikacji, wybierając polecenie wykonywania, takie jak **Rozpocznij debugowanie**, z menu **debugowanie** .

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Aby zaimportować aplikację do istniejącego rozwiązania Visual Studio

1. Przy użyciu C++rozwiązania C#, lub Visual Basic otwartego w programie Visual Studio wybierz pozycję **plik** > **Dodaj** > **istniejący projekt**.

1. W oknie dialogowym **Otwórz projekt** zaznacz opcję **wszystkie pliki projektu**, jeśli nie została jeszcze wybrana, na liście rozwijanej obok pola **Nazwa pliku**.

1. Przejdź do pliku *. exe* , zaznacz go, a następnie wybierz pozycję **Otwórz**.

   Plik pojawi się jako nowy projekt w bieżącym rozwiązaniu.

1. Po wybraniu nowego pliku Rozpocznij debugowanie aplikacji, wybierając polecenie wykonywania, takie jak **Rozpocznij debugowanie**, z menu **debugowanie** .

### <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [DBG, pliki](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))