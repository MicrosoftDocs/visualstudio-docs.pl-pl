---
ms.openlocfilehash: 69f4f4c2b55670d510652b44a203b9f0eafcc53a
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "68143542"
---

1. Zamknij i Otwórz konsolę zarządzania usług IIS, aby wyświetlić zaktualizowaną konfiguracją opcje w interfejsie użytkownika.

2. W usługach IIS, kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, wybierz **Wdróż** > **skonfigurować wdrażanie publikowania w sieci Web**.

    ![Konfigurację narzędzia Web Deploy](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. W **skonfigurować wdrażanie publikowania w sieci Web** okna dialogowego Sprawdź ustawienia.

4. Kliknij przycisk **Instalatora**.

    W **wyniki** panelu pokazano w danych wyjściowych, które uprawnienia są przyznawane określonego użytkownika, a plik z *.publishsettings* rozszerzenie pliku został wygenerowany w lokalizacji przedstawionej w oknie dialogowym pole.

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

    W zależności od konfiguracji systemu Windows Server i usług IIS zostaną wyświetlone różne wartości w pliku XML. Poniżej przedstawiono kilka informacji o wartościach, które są wyświetlane:

   * *Msdeploy.axd* pliku, do którego odwołuje się `publishUrl` atrybut jest dynamicznie generowanych plików programu obsługi HTTP dla narzędzia Web Deploy. (Do celów testowych `http://myhostname:8172` zazwyczaj działa tak dobrze.)
   * `publishUrl` Ustawiony jest port portu 8172, co jest ustawieniem domyślnym dla narzędzia Web Deploy.
   * `destinationAppUrl` Ustawiony jest port 80, port, co jest ustawieniem domyślnym dla usług IIS.
   * Jeśli nie można nawiązać połączenia z hostem zdalnym w programie Visual Studio przy użyciu nazwy hosta (w kolejnych krokach), przetestuj adres IP zamiast nazwy hosta.

     > [!NOTE]
     > W przypadku publikowania w programie IIS działającym na Maszynie wirtualnej platformy Azure, możesz otworzyć narzędzia Web Deploy oraz porty usługi IIS w grupie zabezpieczeń sieci. Aby uzyskać szczegółowe informacje, zobacz [instalacji i uruchomienia usług IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Skopiuj ten plik na komputerze, na którym uruchomiony jest program Visual Studio.
