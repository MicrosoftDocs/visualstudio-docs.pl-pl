---
ms.openlocfilehash: 1e6c6714720d652fff266e3e852d01982c98e34a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173895"
---
Web Deploy 3,6 dla serwerów hostingu oferuje dodatkowe funkcje konfiguracji, które umożliwiają tworzenie pliku ustawień publikowania w interfejsie użytkownika.

1. Jeśli masz już zainstalowaną Web Deploy 3,6 w systemie Windows Server, Odinstaluj **Control Panel**go za pomocą  >  **apletu programy**panelu sterowania  >  **Odinstaluj program**.

2. Następnie zainstaluj Web Deploy 3,6 dla serwerów hostingu w systemie Windows Server.

    Aby zainstalować Web Deploy dla serwerów hostingu, użyj Instalatora platformy sieci Web (Instalatora WebPI). (Aby znaleźć łącze Instalatora platformy sieci Web z usług IIS, wybierz pozycję **IIS** w lewym okienku Menedżer serwera. W okienku serwera kliknij prawym przyciskiem myszy serwer, a następnie wybierz pozycję **menedżer Internet Information Services (IIS)**. Następnie użyj linku **Pobierz nowe składniki platformy sieci Web** w oknie **Akcje** .) Możesz również uzyskać dostęp do Instalatora platformy sieci Web (Instalatora WebPI) z [plików do pobrania](https://www.microsoft.com/web/downloads/platform.aspx).

    W Instalatorze platformy sieci Web Znajdź **Web Deploy 3,6 dla serwerów hostingu** na karcie aplikacje.

3. Jeśli nie zostały jeszcze zainstalowane **Narzędzia i skrypty zarządzania usługami IIS**, zainstaluj je teraz.

    Wybierz kolejno pozycje **serwer**  >  **serwer sieci Web**  >  **Narzędzia do zarządzania**programu, a następnie wybierz rolę **Narzędzia i skrypty zarządzania usługami IIS** , kliknij przycisk **dalej**, a następnie Zainstaluj rolę.

    ![Zainstaluj narzędzia i skrypty zarządzania usługami IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Do włączenia generowania pliku ustawień publikowania wymagane są skrypty i narzędzia.

4. Obowiązkowe Sprawdź, czy Web Deploy działa prawidłowo, otwierając **Panel sterowania > system i zabezpieczenia > narzędzia administracyjne > usługi** i upewnij się, że **Usługa Deployment Agent sieci Web** jest uruchomiona (nazwa usługi jest inna w starszych wersjach).

    Jeśli usługa agenta nie jest uruchomiona, należy ją uruchomić. Jeśli ta aplikacja nie istnieje, przejdź do pozycji **Panel sterowania > programy > Odinstaluj program**, Znajdź pozycję **Microsoft Web Deploy \<version> **. Wybierz opcję **zmiany** instalacji i upewnij się, że wybrana opcja **zostanie zainstalowana na lokalnym dysku twardym** dla składników Web Deploy. Wykonaj kroki instalacji zmian.