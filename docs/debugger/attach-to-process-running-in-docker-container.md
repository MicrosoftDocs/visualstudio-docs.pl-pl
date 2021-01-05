---
title: Dołączanie do procesu działającego w kontenerze platformy Docker
description: Dowiedz się, jak debugować aplikację z uruchomionym kontenerem platformy Docker przy użyciu programu Visual Studio
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: f6e2b851057d924353e6e1e9a211fcbb294353c8
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761267"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Dołączanie do procesu działającego w kontenerze platformy Docker 

Można debugować aplikacje działające w kontenerze platformy Docker systemu Windows lub kontenerze platformy Docker .NET Core przy użyciu programu Visual Studio.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>Dołączanie do procesu działającego w kontenerze platformy Docker systemu Linux

Debuger programu Visual Studio można dołączyć do procesu działającego w kontenerze Docker platformy Linux .NET Core na komputerze lokalnym lub zdalnym przy użyciu okna dialogowego **Dołącz do procesu** .

> [!IMPORTANT]
> Aby użyć tej funkcji, należy zainstalować środowisko programistyczne dla wielu platform .NET Core i mieć lokalny dostęp do kodu źródłowego.

**Aby dołączyć do uruchomionego procesu w kontenerze platformy Docker systemu Linux:**

1. W programie Visual Studio wybierz kolejno opcje **debuguj > Dołącz do procesu (Ctrl + Alt + P)** , aby otworzyć okno dialogowe **Dołącz do procesu** .

![Zrzut ekranu przedstawiający okno dialogowe Dołączanie do procesu w programie Visual Studio z informacją o typie połączenia platformy Docker (kontener systemu Linux).](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Ustaw **Typ połączenia** na **Docker (kontener systemu Linux)**.
3. Wybierz pozycję **Znajdź...** , aby ustawić **cel połączenia** za pomocą okna dialogowego **Wybieranie kontenera platformy Docker** .

    Proces kontenera Docker można debugować lokalnie lub zdalnie.

    **Aby debugować proces kontenera platformy Docker lokalnie:**
    1. Ustaw **hosta interfejsu wiersza polecenia platformy Docker** na **maszynę lokalną**.
    1. Wybierz uruchomiony kontener do dołączenia z listy i kliknij przycisk **OK**.

    ![Wybierz menu kontenera platformy Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. Aby debugować proces kontenera platformy Docker zdalnie:**

    > [!NOTE]
    > Dostępne są dwie opcje łączenia zdalnego z uruchomionym procesem w kontenerze platformy Docker. Pierwsza opcja, aby korzystać z protokołu SSH, jest idealna, jeśli nie masz zainstalowanych narzędzi platformy Docker na komputerze lokalnym.  Jeśli masz zainstalowane narzędzia platformy Docker lokalnie i masz demona platformy Docker, która jest skonfigurowana do akceptowania żądań zdalnych, wypróbuj drugą opcję przy użyciu demona Docker.

    1. **_Aby nawiązać połączenie z komputerem zdalnym za pośrednictwem protokołu SSH:_* _
        1. Wybierz _ *Dodaj...* * Aby nawiązać połączenie z systemem zdalnym.<br/>
        ![Nawiązywanie połączenia z systemem zdalnym](../debugger/media/connect-remote-system.png "Nawiązywanie połączenia z systemem zdalnym")
        1. Wybierz uruchomiony kontener do dołączenia po pomyślnym nawiązaniu połączenia z protokołem SSH lub demonem, a następnie naciśnij przycisk **OK**.

    1. **_Aby ustawić docelowy kontener zdalny, na którym działa proces za pośrednictwem [demona Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)_* _
        1. Określ adres demona (tj. za pośrednictwem protokołu TCP, IP itp.) w obszarze _ *hosta platformy Docker (opcjonalnie)** i kliknij link odświeżenia.
        1. Wybierz uruchomiony kontener do dołączenia po pomyślnym nawiązaniu połączenia z demonem, a następnie naciśnij przycisk **OK**.

4. Wybierz odpowiedni proces kontenera z listy **dostępnych procesów** , a następnie wybierz pozycję **Dołącz** , aby rozpocząć debugowanie procesu kontenera języka C# w programie Visual Studio.

    ![Zrzut ekranu przedstawiający okno dialogowe Dołączanie do procesu w programie Visual Studio. Typ połączenia jest ustawiony na Docker (kontener systemu Linux), a wybrano proces dotnet.](../debugger/media/docker-attach-complete.png "Ukończono menu dołączania Docker systemu Linux")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>Dołączanie do procesu działającego w kontenerze platformy Docker systemu Windows

Debuger programu Visual Studio można dołączyć do procesu działającego w kontenerze platformy Docker systemu Windows na komputerze lokalnym przy użyciu okna dialogowego **Dołącz do procesu** .

> [!IMPORTANT]
> Aby użyć tej funkcji w procesie .NET Core, należy zainstalować Międzyplatformowe obciążenie dla programu .NET Core i uzyskać lokalny dostęp do kodu źródłowego.

**Aby dołączyć do uruchomionego procesu w kontenerze platformy Docker systemu Windows:**

1. W programie Visual Studio wybierz kolejno opcje **debuguj > Dołącz do procesu** (lub **Ctrl + Alt + P**), aby otworzyć okno dialogowe **Dołącz do procesu** .

   ![Zrzut ekranu przedstawiający okno dialogowe Dołączanie do procesu w programie Visual Studio z informacją o typie połączenia platformy Docker (kontener systemu Windows).](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Ustaw **Typ połączenia** na **Docker (kontener systemu Windows)**.
3. Wybierz pozycję **Znajdź...** , aby ustawić **cel połączenia** przy użyciu okna dialogowego **Wybieranie kontenera platformy Docker** .

    > [!IMPORTANT]
    > Proces docelowy musi mieć taką samą architekturę procesora jak kontener systemu Windows platformy Docker, na którym działa.

   Ustawienie obiektu docelowego na kontener zdalny za pośrednictwem protokołu SSH jest obecnie niedostępne i można go wykonać tylko przy użyciu demona platformy Docker.

    **_Aby ustawić docelowy kontener zdalny, na którym działa proces za pośrednictwem [demona Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)_* _
    1. Określ adres demona (tj. za pośrednictwem protokołu TCP, IP itp.) w obszarze _ *hosta platformy Docker (opcjonalnie)** i kliknij link odświeżenia.

    1. Wybierz uruchomiony kontener do dołączenia po pomyślnym nawiązaniu połączenia z demonem, a następnie wybierz przycisk OK.

4. Wybierz odpowiedni proces kontenera z listy **dostępnych procesów** , a następnie wybierz pozycję **Dołącz** , aby rozpocząć debugowanie procesu kontenera języka C#.

    ![Zrzut ekranu przedstawiający okno dialogowe Dołączanie do procesu w programie Visual Studio. Typ połączenia jest ustawiony na Docker (kontener systemu Windows), a wybrano proces dotnet.exe.](../debugger/media/docker-attach-complete-windows.png "Zakończono menu dołączania Docker systemu Windows")

5. Wybierz odpowiedni proces kontenera z listy dostępnych procesów, a następnie wybierz pozycję **Dołącz** , aby rozpocząć debugowanie procesu kontenera języka C#.