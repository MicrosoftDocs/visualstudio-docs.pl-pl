---
title: Ustaw uprawnienia | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: f0a55e5e18829856b913ad01df6f831a2df42863
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851830"
---
# <a name="how-to-set-permissions"></a>Instrukcje: Ustawianie uprawnień

W tym artykule opisano, jak administrator komputera przyznaje uprawnienia zabezpieczeń wymagane do profilowania użytkownikowi lub grupie, która nie ma uprawnień administratora na tym komputerze.

Podstawowa zasada zabezpieczeń określa, że aplikacje powinny być uruchamiane bez dodatkowych uprawnień. Ta zasada ma zastosowanie również do użytkowników. Jeśli użytkownicy mogą być w pełni wydajni, gdy są zalogowani jako członkowie grupy Użytkownicy zamiast grupy Administratorzy, nie powinni mieć uprawnień administratora. Pierwsza procedura "aby utworzyć konto użytkownika z uprawnieniami użytkownika" zawiera opis sposobu tworzenia konta użytkownika dla członka grupy użytkowników.

Członkowie grupy Użytkownicy będą musieli mieć dostęp do folderów i plików na dysku, które są udostępniane innym członkom zespołu. Druga procedura "aby udzielić dostępu do udostępnionych plików projektu" zawiera opis sposobu udzielania dostępu.

Członkowie grupy Użytkownicy mogą uruchamiać narzędzia profilowania, jeśli administrator udzieli im dostępu do sterownika oprogramowania dla narzędzi profilowania. Ostatnia procedura "aby udzielić dostępu do sterownika profilowania" opisuje sposób udzielania dostępu do tego sterownika.

> [!NOTE]
> Aby wykonać kroki opisane w tych procedurach, musisz mieć uprawnienia administratora.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>Aby utworzyć konto użytkownika, które ma uprawnienia użytkownika

1. Kliknij prawym przyciskiem myszy pozycję **mój komputer** , a następnie kliknij pozycję **Zarządzaj**.

     Zostanie otwarte okno **Zarządzanie komputerem** .

2. Rozwiń węzeł **lokalni użytkownicy i grupy**.

3. Kliknij prawym przyciskiem myszy folder **Użytkownicy** , a następnie kliknij polecenie **nowy użytkownik**.

     Zostanie wyświetlone okno dialogowe **nowy użytkownik** .

4. Wypełnij pola w tym oknie dialogowym informacjami o tworzonym koncie użytkownika. Określ hasło. Opcjonalnie zaznacz pole wyboru, które wymaga zmiany hasła przy następnym logowaniu.

5. Kliknij przycisk **Utwórz** , a następnie kliknij przycisk **Zamknij**.

     Nowy użytkownik zostanie wyświetlony w grupie Użytkownicy, grupy użytkowników, którzy nie mają uprawnień administratora.

## <a name="to-grant-access-to-shared-project-files"></a>Aby udzielić dostępu do udostępnionych plików projektu

1. W Eksploratorze Windows (lub Eksploratorze plików) zlokalizuj katalog główny drzewa folderów dla plików projektu używanych przez tego użytkownika i udostępnionych przez zespół projektu.

     Ścieżka tego folderu może wyglądać następująco:

    ```cmd
    D:\ourProject
    ```

2. Kliknij prawym przyciskiem myszy folder, a następnie kliknij polecenie **Właściwości**.

     Zostanie wyświetlone okno dialogowe ** \<folder name> Właściwości** .

3. Kliknij kartę **Zabezpieczenia**.

4. Kliknij nazwę konta użytkownika w polu **Nazwa grupy lub użytkownika** .

5. W polu **uprawnienia dla \<user name> ** zaznacz pole wyboru **pełna kontrola**.

6. Kliknij przycisk **OK**.

     To przyznaje użytkownikowi uprawnienia do udostępnionego drzewa folderów, które rozpoczyna się od folderu wybranego w kroku 5.

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

     To polecenie służy do instalowania i uruchamiania sterownika dla narzędzi profilowania.

     To polecenie uruchamia sterownik profilowania i usługę, dzięki czemu użytkownicy niebędący administratorami mogą korzystać z funkcji profilowania, które są dostępne w obszarze procesu użytkownika. Tylko administrator może uruchomić polecenie; i nie będą działać dla użytkowników niebędących administratorami.

     Należy zauważyć, że skutki tego kroku są cofnięte po ponownym uruchomieniu komputera, chyba że zostanie również wykonany ostatni krok tej procedury.

4. Uruchom polecenie, aby zezwolić na dostęp do profilowania funkcji sterownika przez użytkownika lub grupę, która nie ma dostępu administratora do komputera:

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     To polecenie przyznaje \<user name> \<group name> dostęp do narzędzi profilowania lub kontu. \<right>Opcja określa funkcje profilowania, do których użytkownik może uzyskać dostęp. \<right>Opcja może mieć jedną lub więcej z następujących wartości:

    - FullAccess — umożliwia dostęp do wszystkich metod profilowania, w tym zbierania danych o wydajności z usług, pobierania próbek i profilowania sesji między sesjami.

    - SampleProfiling — umożliwia dostęp do przykładowych metod profilowania

    - CrossSession — umożliwia dostęp do profilowania między sesjami, które są wymagane do profilowania usług.

5. Obowiązkowe Aby zachować wyniki dowolnego z poprzednich kroków po ponownym uruchomieniu komputera, uruchom następujące polecenie:

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   Określeni użytkownicy po zalogowaniu się będą mogli korzystać z narzędzi profilowania bez uprawnień administratora.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md) 
 [VSPerfCmd](../profiling/vsperfcmd.md) 
 [Profilowanie i zabezpieczenia systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)
