---
title: Debugowanie aplikacji, która nie jest częścią rozwiązania programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak debugować aplikację, która nie jest częścią rozwiązania programu Visual Studio. Może być możliwe dołączenie debugera programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/21/2020
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f201121eb65f7c045ac42783ac71b2d49fafd802
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155006"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Debugowanie aplikacji, która nie jest częścią rozwiązania programu Visual Studio (C++, C#, Visual Basic, F #)

Możesz chcieć debugować aplikację (plik *exe* ), która nie jest częścią rozwiązania programu Visual Studio. Może to być [otwarty projekt folderu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) lub ktoś inny mógł utworzyć aplikację poza programem Visual Studio lub uzyskać aplikację z innej lokalizacji.

- W przypadku projektu otwartego folderu w programie Visual Studio (który nie ma pliku projektu lub rozwiązania), zobacz [Uruchamianie i debugowanie kodu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) lub, w przypadku języka C++, [Konfigurowanie parametrów debugowania z launch.vs.json](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- W przypadku aplikacji, która nie istnieje w programie Visual Studio, typowym sposobem debugowania jest uruchomienie aplikacji poza programem Visual Studio, a następnie dołączenie do niej przy użyciu opcji **Dołącz do procesu** w debugerze programu Visual Studio. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Dołączanie do aplikacji wymaga ręcznego wykonania czynności, które potrwają kilka sekund. Z tego powodu nie można dołączać do debugowania problemu z uruchamianiem ani aplikacji, która nie czeka na dane wejściowe użytkownika i kończy się szybko.

   W takich sytuacjach można utworzyć projekt Visual Studio EXE dla aplikacji lub zaimportować go do istniejącego rozwiązania C#, Visual Basic lub C++. Nie wszystkie języki programowania obsługują projekty EXE.

>[!IMPORTANT]
>Funkcje debugowania dla aplikacji, która nie została wbudowana w programie Visual Studio, są ograniczone, niezależnie od tego, czy dołączysz do aplikacji, czy dodajesz ją do rozwiązania programu Visual Studio.
>
>Jeśli masz kod źródłowy, najlepszym rozwiązaniem jest zaimportowanie kodu do projektu programu Visual Studio. Następnie uruchom kompilację debugowania aplikacji.
>
>Jeśli nie masz kodu źródłowego, a aplikacja nie ma [informacji debugowania](../debugger/how-to-set-debug-and-release-configurations.md) w zgodnym formacie, dostępne funkcje debugowania są bardzo mało.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Aby utworzyć nowy projekt EXE dla istniejącej aplikacji

1. W programie Visual Studio wybierz pozycję **plik**  >  **Otwórz**  >  **projekt**.

1. W oknie dialogowym **Otwórz projekt** zaznacz opcję **wszystkie pliki projektu**, jeśli nie została jeszcze wybrana, na liście rozwijanej obok pola **Nazwa pliku**.

1. Przejdź do pliku *. exe* , zaznacz go, a następnie wybierz pozycję **Otwórz**.

   Plik pojawi się w nowym, tymczasowym rozwiązaniu programu Visual Studio.

1. Rozpocznij debugowanie aplikacji, wybierając polecenie wykonywania, takie jak **Rozpocznij debugowanie**, z menu **debugowanie** .

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Aby zaimportować aplikację do istniejącego rozwiązania programu Visual Studio

1. W programie Visual Studio z otwartym rozwiązaniem języka C++, C# lub Visual Basic wybierz pozycję **plik**  >  **Dodaj**  >  **istniejący projekt**.

1. W oknie dialogowym **Otwórz projekt** zaznacz opcję **wszystkie pliki projektu**, jeśli nie została jeszcze wybrana, na liście rozwijanej obok pola **Nazwa pliku**.

1. Przejdź do pliku *. exe* , zaznacz go, a następnie wybierz pozycję **Otwórz**.

   Plik jest wyświetlany jako nowy projekt w ramach bieżącego rozwiązania.

1. Po wybraniu nowego pliku Rozpocznij debugowanie aplikacji, wybierając polecenie wykonywania, takie jak **Rozpocznij debugowanie**, z menu **debugowanie** .

### <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [DBG, pliki](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))
