---
ms.openlocfilehash: b8002d9e911c8d8c07a5aaf5286168e49a374a7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85292099"
---

1. Zamknij i ponownie otwórz konsolę zarządzania usługami IIS, aby wyświetlić zaktualizowane opcje konfiguracji w interfejsie użytkownika.

2. W programie IIS kliknij prawym przyciskiem myszy **domyślną witrynę sieci Web**, wybierz polecenie **Wdróż**  >  **Skonfiguruj Web Deploy publikowanie**.

    ![Konfigurowanie konfiguracji Web Deploy](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

   Jeśli nie widzisz menu **Deploy** , zapoznaj się z poprzednią sekcją, aby sprawdzić, czy Web Deploy jest uruchomiona.

3. W oknie dialogowym **Konfigurowanie publikowania Web Deploy** przejrzyj ustawienia.

4. Kliknij przycisk **Setup (Konfiguracja**).

    W panelu **wyników** dane wyjściowe pokazują, że prawa dostępu są udzielane określonemu użytkownikowi i że plik z rozszerzeniem *. publishsettings* został wygenerowany w lokalizacji pokazanej w oknie dialogowym.

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

    W zależności od konfiguracji systemu Windows Server i usług IIS zobaczysz różne wartości w pliku XML. Poniżej przedstawiono kilka szczegółowych informacji o wartościach, które są widoczne:

   * Plik *MSDeploy. axd* , do którego odwołuje się ten `publishUrl` atrybut jest dynamicznie generowanym plikiem programu obsługi HTTP dla Web Deploy. (Na potrzeby testowania `http://myhostname:8172` zazwyczaj działa również).
   * `publishUrl`Port jest ustawiony na port 8172, który jest wartością domyślną dla Web Deploy.
   * `destinationAppUrl`Port jest ustawiony na port 80, który jest wartością domyślną dla usług IIS.
   * Jeśli nie można nawiązać połączenia z hostem zdalnym w programie Visual Studio przy użyciu nazwy hosta (w dalszych krokach), Przetestuj adres IP zamiast nazwy hosta.

     > [!NOTE]
     > W przypadku publikowania w usługach IIS działających na maszynie wirtualnej platformy Azure należy otworzyć Web Deploy i porty usług IIS w sieciowej grupie zabezpieczeń. Aby uzyskać szczegółowe informacje, zobacz [Instalowanie i uruchamianie usług IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Skopiuj ten plik na komputer, na którym jest uruchomiony program Visual Studio.
