---
ms.openlocfilehash: 0fc18fab56f5b46ef097cdf699e4f0569dc190c9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143522"
---
Web Deploy 3.6 for Hosting Servers zapewnia dodatkowe funkcje konfiguracyjne, które umożliwiają tworzenie pliku ustawień publikowania z interfejsu użytkownika.

1. Jeśli w systemie Windows Server zainstalowano już program Web Deploy 3.6, odinstaluj go za pomocą**programów** >  **Panelu sterowania** > **Odinstaluj program**.

2. Następnie zainstaluj program Web Deploy 3.6 dla serwerów hostingowych w systemie Windows Server.

    Aby zainstalować program Web Deploy for Hosting Servers, użyj [instalatora platformy sieci Web (WebPI).](https://www.microsoft.com/web/downloads/platform.aspx) (Aby znaleźć łącze Instalatora platformy sieci Web z usług IIS, wybierz **usługi IIS** w lewym okienku Menedżera serwera. Kliknij prawym przyciskiem myszy serwer i wybierz **menedżera internetowych usług informacyjnych (IIS).**

    W Instalatorze platformy sieci Web znajdziesz **pozycję Wdrażanie sieci Web dla serwerów hostingowych** na karcie Aplikacje.

3. Jeśli nie zainstalowano jeszcze **skryptów i narzędzi zarządzania usługami IIS,** zainstaluj je teraz.

    Przejdź do pozycji Narzędzia do**zarządzania****serwerami sieci Web (IIS)** >  **wybierz pozycję Wybierz role** > serwerów sieci Web ,a następnie wybierz rolę **Skrypty i narzędzia zarządzania usługami IIS,** kliknij przycisk **Dalej**, a następnie zainstaluj rolę.

    ![Instalowanie skryptów i narzędzi zarządzania usługami IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Skrypty i narzędzia są wymagane, aby umożliwić generowanie pliku ustawień publikowania.

4. (Opcjonalnie) Sprawdź, czy wdrażanie w sieci Web działa poprawnie, otwierając **Panel sterowania > system i narzędzia administracyjne > zabezpieczeń > usługami** i upewnij się, że usługa **agenta wdrażania sieci Web** jest uruchomiona (nazwa usługi jest inna w starszych wersjach).

    Jeśli usługa agenta nie jest uruchomiona, uruchom ją. Jeśli w ogóle nie jest obecny, przejdź do **panelu sterowania > programy > Odinstaluj program**, znajdź wersję microsoft Web Deploy ** \<>**. Wybierz **opcję Zmień** instalację i upewnij się, że wybierz pozycję **Zostanie zainstalowany na lokalnym dysku twardym** dla składników wdrażania w sieci Web. Wykonaj kroki instalacji zmiany.