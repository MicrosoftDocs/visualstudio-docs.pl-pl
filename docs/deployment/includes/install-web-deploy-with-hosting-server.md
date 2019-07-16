---
ms.openlocfilehash: 0fc18fab56f5b46ef097cdf699e4f0569dc190c9
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "68143522"
---
Narzędzie Web Deploy 3.6 dla serwerów do hostingu udostępnia funkcje dodatkowe czynności konfiguracyjne, które umożliwiają tworzenie pliku ustawień publikowania w interfejsie użytkownika.

1. Jeśli masz już zainstalowany w systemie Windows Server 3.6 wdrażania sieci Web, odinstaluj je za pomocą **Panelu sterowania** > **programy** > **Odinstaluj Program**.

2. Następnie zainstaluj 3.6 wdrażania sieci Web dla serwerów do hostingu w systemie Windows Server.

    Aby zainstalować narzędzie Web Deploy dla serwerów do hostingu, użyj [Instalatora platformy sieci Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Aby znaleźć link Instalatora platformy sieci Web za pomocą programu IIS, wybierz **IIS** w okienku po lewej stronie w Menedżerze serwera. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz pozycję **Internet Information Services (IIS) Manager**.)

    W oknie Instalatora platformy sieci Web możesz znaleźć **Web Deploy dla serwerów do hostingu** na karcie aplikacje.

3. Jeśli nie został jeszcze zainstalowany **narzędzia i skrypty zarządzania usługami IIS**, zainstalowanie go teraz.

    Przejdź do **Wybieranie ról serwera** > **serwer sieci Web (IIS)**  > **narzędzia do zarządzania**, a następnie wybierz pozycję **skrypty zarządzania usługami IIS Narzędzia i** roli, kliknij przycisk **dalej**, a następnie zainstaluj rolę.

    ![Zainstaluj narzędzia i skrypty zarządzania usługami IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Skrypty i narzędzia są wymagane, aby umożliwić wygenerowanie dyrektyw plik ustawień publikowania.

4. (Opcjonalnie) Sprawdź, czy narzędzie Web Deploy działa poprawnie, otwierając **Panel sterowania > System i Zabezpieczenia > Narzędzia administracyjne > usługi** i upewnij się, że **Usługa agenta wdrażania sieci Web** działa ( Nazwa usługi jest inny w starszych wersjach).

    Jeśli nie jest uruchomiona usługa agenta, należy ją uruchomić. Jeśli nie ma go na wszystkich, przejdź do strony **Panel sterowania > programy > Odinstaluj program**, Znajdź **Microsoft Web Deploy \<wersji >** . Możliwość **zmiany** instalacji i upewnij się, że wybierasz **zostanie zainstalowana na lokalnym dysku twardym** składników Web Deploy. Wykonaj kroki instalacji zmiany.