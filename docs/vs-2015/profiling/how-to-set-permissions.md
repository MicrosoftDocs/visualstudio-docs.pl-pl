---
title: 'Instrukcje: Ustaw uprawnienia | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
ms.assetid: 69f27896-8f46-4ef3-bfb7-726d95304f3a
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61276307516052673f07a6798673b9998cb609fb
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54833839"
---
# <a name="how-to-set-permissions"></a>Instrukcje: Ustawianie uprawnień
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano, jak Administrator komputera przyznaje uprawnienia zabezpieczeń wymagane do profilowania do użytkownika lub grupy, która nie ma uprawnienia administratora na tym komputerze.  
  
 Zasady zabezpieczeń podstawowych stanów, aplikacje powinny być uruchamiane z nie więcej niż uprawnienia, które są im potrzebne. Ta zasada ma zastosowanie także do użytkowników. Jeśli użytkownicy mogą być w pełni obowiązywać, gdy jest zalogowany jako członkowie grupy użytkowników, zamiast do grupy Administratorzy, ich może nie być przyznany uprawnienia administratora. Pierwszej procedury "Aby utworzyć konto użytkownika, które ma uprawnienia użytkownika" w tym artykule opisano sposób tworzenia konta użytkownika dla członka grupy użytkowników.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Członkowie grupy Użytkownicy będą potrzebowali dostępu do folderów i plików na dysku, które są współużytkowane z innymi członkami zespołu. Drugą procedurę "Aby udzielić dostępu do plików projektu udostępnionego" w tym artykule opisano jak przyznać dostęp.  
  
  Jeśli administrator przyznaje im dostęp do sterownika oprogramowania dla narzędzi profilowania, członkowie grupy użytkowników można uruchomić narzędzi profilowania. Ostatniej procedury "Aby udzielić dostępu do profilowania sterownika" w tym artykule opisano jak udzielić dostępu do tego sterownika.  
  
> [!NOTE]
>  Musisz mieć uprawnienia administratora, aby wykonać czynności opisane w tych procedurach.  
  
### <a name="to-create-a-user-account-that-has-user-permissions"></a>Aby utworzyć konto użytkownika, które ma uprawnienia użytkownika  
  
1.  Kliknij prawym przyciskiem myszy **Mój komputer** a następnie kliknij przycisk **Zarządzaj**.  
  
     **Zarządzanie komputerem** zostanie otwarte okno.  
  
2.  Rozwiń **lokalnych użytkowników i grup**.  
  
3.  Kliknij prawym przyciskiem myszy **użytkowników** folder, a następnie kliknij przycisk **nowego użytkownika**.  
  
     **Nowego użytkownika** pojawi się okno dialogowe.  
  
4.  Wypełnij pola w oknie dialogowym z informacjami dla konta użytkownika, czy tworzysz. Określ hasło. Opcjonalnie zaznacz pole wyboru, które wymaga, aby zmiany hasła przy następnym logowaniu użytkownika.  
  
5.  Kliknij przycisk **Utwórz** a następnie kliknij przycisk **Zamknij**.  
  
     Nowy użytkownik pojawi się w grupie Użytkownicy, grupy użytkowników, którzy nie mają uprawnień administratora.  
  
### <a name="to-grant-access-to-shared-project-files"></a>Aby udzielić dostępu do udostępnionych plików projektu  
  
1.  W Eksploratorze Windows (lub Eksploratora plików) Znajdź katalog główny drzewa folder dla projektu pliki używane przez tego użytkownika i udostępnione przez zespół projektu.  
  
     Ścieżka tego folderu może wyglądać w następujący sposób:  
  
    ```  
    D:\ourProject  
    ```  
  
2.  Kliknij prawym przyciskiem myszy folder, a następnie kliknij przycisk **właściwości**.  
  
     **\<Nazwę folderu > właściwości** pojawi się okno dialogowe.  
  
3.  Kliknij przycisk **zabezpieczeń** kartę.  
  
4.  Kliknij nazwę konta w **nazwy grupy lub użytkownika** pole.  
  
5.  W **uprawnienia dla \<nazwa użytkownika >** zaznacz pole wyboru dla **Pełna kontrola**.  
  
6.  Kliknij przycisk **OK**.  
  
     Spowoduje to przydzielenie uprawnień dla użytkownika na potrzeby drzewa folder udostępniony, który rozpoczyna się od folderu wybrana w kroku 5.  
  
### <a name="to-grant-access-to-the-profiling-driver"></a>Aby udzielić dostępu do profilowania sterownika  
  
1. Otwórz wiersz polecenia jako administrator.  
  
2. Zmień katalog na:  
  
   ```  
   <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools  
   ```  
  
3. Uruchom następujące polecenie:  
  
   ```  
   vsperfcmd /admin:driver,start /admin:service,start  
   ```  
  
    To polecenie instaluje i uruchamia sterownik dla narzędzi profilowania.  
  
    To polecenie uruchamia profilowanie sterowników i usługi, aby użytkownicy inni niż administratorzy mogą używać profilowania funkcji, które są dostępne w przestrzeni procesu ich użytkowników. Tylko Administrator może uruchomić polecenia; i nie powiedzie się dla użytkowników innych niż administracyjne.  
  
    Należy zauważyć, że efekty w tym kroku są cofnięta po ponownym uruchomieniu komputera, chyba że również wykonać ostatni krok w tej procedurze.  
  
4. Uruchom polecenie, aby zezwolić na dostęp do profilowania funkcji sterownika przez użytkownika lub grupy, które ma dostęp administratora do komputera:  
  
   ```  
   vsperfcmd /admin:security,allow,<right[,right],<user name|group name>  
   ```  
  
    To polecenie przyznaje \<nazwa_użytkownika > lub \<Nazwa grupy > konta dostępu do narzędzi profilowania. \<Prawo > Opcja określa profilowania funkcji użytkownik może uzyskać dostęp. \<Prawo > opcja może być co najmniej jeden z następujących wartości:  
  
   -   FullAccess — zezwala na dostęp do wszystkich metod profilowania, zbieranie danych wydajności z usługi, w tym do pobierania próbek i obejmujące wiele sesji profilowania.  
  
   -   SampleProfiling — zezwala na dostęp do metod profilowania próbki  
  
   -   CrossSession — zezwala na dostęp do wielu sesji profilowania, co jest wymagane dla usług profilowania.  
  
5. (Opcjonalnie) Aby zachować wyniki dowolnego z poprzednich kroków, po ponownym uruchomieniu komputera, uruchom następujące polecenie:  
  
   ```  
   vsperfcmd /admin:driver,autostart,on  
   ```  
  
   Określeni użytkownicy po zalogowaniu, teraz będzie można użyć narzędzi profilowania bez uprawnień administratora.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie i bezpieczeństwo systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md)
