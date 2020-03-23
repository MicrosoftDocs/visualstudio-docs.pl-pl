---
title: 'Jak: Ustawianie uprawnień | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c1ab7705c7ab46b07b08b707ce447f37c581036a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774592"
---
# <a name="how-to-set-permissions"></a>Jak: Ustawianie uprawnień

W tym artykule opisano, jak administrator komputera udziela uprawnień zabezpieczeń wymaganych do profilowania użytkownikowi lub grupie, która nie ma uprawnień administratora na tym komputerze.

Podstawowa zasada zabezpieczeń stanowi, że aplikacje powinny być uruchamiane z nie więcej niż uprawnienia, których potrzebują. Zasada ta ma również zastosowanie do użytkowników. Jeśli użytkownicy mogą być w pełni skuteczni, gdy są zalogowani jako członkowie grupy Użytkownicy, a nie administratorzy, nie należy im przyznawać uprawnień administratora. Pierwsza procedura "Aby utworzyć konto użytkownika, które ma uprawnienia użytkownika", opisano sposób tworzenia konta użytkownika dla członka grupy Użytkownicy.

Członkowie grupy Użytkownicy będą potrzebować dostępu do folderów i plików na dysku, które są udostępniane innym członkom zespołu. Druga procedura "Aby udzielić dostępu do udostępnionych plików projektu", opisuje sposób przyznania tego dostępu.

Członkowie grupy Użytkownicy mogą uruchamiać narzędzia profilowania, jeśli administrator udzieli im dostępu do sterownika oprogramowania dla narzędzi profilowania. Ostatnia procedura "Aby udzielić dostępu do sterownika profilowania", opisuje sposób udzielania dostępu do tego sterownika.

> [!NOTE]
> Aby wykonać kroki opisane w tych procedurach, potrzebne są uprawnienia administratora.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Aby utworzyć konto użytkownika z uprawnieniami użytkownika

1. Kliknij prawym przyciskiem myszy **pozycję Mój komputer,** a następnie kliknij polecenie **Zarządzaj**.

     Zostanie otwarte okno **Zarządzanie komputerem.**

2. Rozwiń **pozycję Użytkownicy i grupy lokalne**.

3. Kliknij prawym przyciskiem myszy folder **Użytkownicy,** a następnie kliknij polecenie **Nowy użytkownik**.

     Zostanie wyświetlone okno dialogowe **Nowy użytkownik.**

4. Uzupełnij pola w tym oknie dialogowym informacjami o utworzeniu konta użytkownika. Określ hasło. Opcjonalnie zaznacz pole wyboru, które wymaga, aby użytkownik zmienił hasło przy następnym logowaniu.

5. Kliknij **pozycję Utwórz,** a następnie kliknij przycisk **Zamknij**.

     Nowy użytkownik pojawia się w grupie Użytkownicy, grupie użytkowników, którzy nie mają uprawnień administratora.

## <a name="to-grant-access-to-shared-project-files"></a>Aby udzielić dostępu do udostępnionych plików projektu

1. W Eksploratorze Windows (lub Eksploratorze plików) znajdź katalog główny drzewa folderów dla plików projektu używanych przez tego użytkownika i udostępnionych przez zespół projektu.

     Ścieżka tego folderu może przypominać następujące elementy:

    ```cmd
    D:\ourProject
    ```

2. Kliknij prawym przyciskiem myszy folder, a następnie kliknij polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe ** \<Właściwości> folderu.**

3. Kliknij kartę **Zabezpieczenia**.

4. Kliknij nazwę konta użytkownika w polu **Grupa lub nazwy użytkowników.**

5. W polu **Uprawnienia \<do>nazwy użytkownika** zaznacz pole wyboru Pełna **kontrola**.

6. Kliknij przycisk **OK**.

     Daje to użytkownikowi uprawnienia do drzewa folderów udostępnionych, które rozpoczyna się od folderu wybranego w kroku 5.

## <a name="to-grant-access-to-the-profiling-driver"></a>Aby udzielić dostępu do sterownika profilowania

1. Otwórz wiersz polecenia jako administrator.

2. Zmień katalog na:

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. Uruchom następujące polecenie:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     To polecenie instaluje i uruchamia sterownik dla narzędzi profilowania.

     To polecenie uruchamia sterownik profilowania i usługę, dzięki czemu użytkownicy niebędący administratorami mogą korzystać z funkcji profilowania, które są dostępne w ich przestrzeni procesu użytkownika. Tylko administrator może uruchomić polecenie; i nie powiedzie się dla użytkowników nieadawidualnych.

     Należy zauważyć, że efekty tego kroku są cofnięte po ponownym uruchomieniu komputera, chyba że wykonasz również ostatni krok w tej procedurze.

4. Uruchom polecenie, aby zezwolić użytkownikowi lub grupie, która nie ma dostępu administratora do komputera, zezwalaj na dostęp do funkcji sterownika profilowania:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     To polecenie \<udziela> nazwy użytkownika \<lub nazwy grupy> dostęp do konta do narzędzi profilowania. Właściwa \<opcja> określa funkcje profilowania, do które użytkownik może uzyskać dostęp. Właściwą \<opcją> może być jedna lub więcej z następujących wartości:

    - FullAccess — umożliwia dostęp do wszystkich metod profilowania, w tym zbierania danych o wydajności z usług, próbkowania i profilowania krzyżowego sesji.

    - SampleProfiling - umożliwia dostęp do metod profilowania próbek

    - CrossSession - umożliwia dostęp do profilowania krzyżowego sesji, który jest wymagany do profilowania usług.

5. (Opcjonalnie) Aby zachować wyniki któregokolwiek z poprzednich kroków po ponownym uruchomieniu komputera, uruchom następujące polecenie:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Po zalogowaniu się określone użytkownicy będą mogli korzystać z narzędzi profilowania bez uprawnień administratora.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji](../profiling/configuring-performance-sessions.md)
wydajności[VSPerfCmd](../profiling/vsperfcmd.md)
[Profilowanie i Zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)
