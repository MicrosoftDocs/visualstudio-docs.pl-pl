---
ms.openlocfilehash: 69f4f4c2b55670d510652b44a203b9f0eafcc53a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143542"
---

1. Zamknij i ponownie otwórz konsolę zarządzania usługami IIS, aby wyświetlić zaktualizowane opcje konfiguracji w interfejsie użytkownika.

2. W serwisach IIS kliknij prawym przyciskiem myszy **domyślną witrynę sieci Web**, wybierz polecenie **Wdrażanie** > **konfigurowania wdrażania narzędzia Web Deploy .**

    ![Konfigurowanie konfiguracji wdrażania sieci Web](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. W oknie dialogowym **Konfigurowanie publikowania wdrażania sieci Web** sprawdź ustawienia.

4. Kliknij **pozycję Ustawienia**.

    W panelu **Wyniki** dane wyjściowe pokazują, że prawa dostępu są przyznawane określonej użytkownikowi oraz że plik z rozszerzeniem pliku *.publishsettings* został wygenerowany w lokalizacji pokazanej w oknie dialogowym.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    W zależności od konfiguracji systemu Windows Server i usług IIS w pliku XML są widoczne różne wartości. Oto kilka szczegółów dotyczących wartości, które widzisz:

   * Plik *msdeploy.axd,* do `publishUrl` którego odwołuje się atrybut, jest dynamicznie generowanym plikiem obsługi HTTP dla wdrażania w sieci Web. (Do celów testowych, `http://myhostname:8172` ogólnie działa również.)
   * Port `publishUrl` jest ustawiony na port 8172, który jest domyślny dla wdrożenia w sieci Web.
   * Port `destinationAppUrl` jest ustawiony na port 80, który jest domyślny dla IIS.
   * Jeśli nie można połączyć się z hostem zdalnym w programie Visual Studio przy użyciu nazwy hosta (w późniejszych krokach), przetestuj adres IP zamiast nazwy hosta.

     > [!NOTE]
     > Jeśli publikujesz w usługach IIS uruchomionych na maszynie Wirtualnej platformy Azure, musisz otworzyć porty wdrażania w sieci Web i usług IIS w grupie Zabezpieczenia sieciowe. Aby uzyskać szczegółowe informacje, zobacz [Instalowanie i uruchamianie usługi IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Skopiuj ten plik na komputer, na którym jest uruchomiony program Visual Studio.
