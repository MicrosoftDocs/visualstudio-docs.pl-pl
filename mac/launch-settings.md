---
title: uruchom pomoc techniczną dla firmSettings.json
description: Ten dokument obejmuje obsługę launchSettings.json w programie Visual Studio dla komputerów Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715931"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Podczas opracowywania projektów ASP.NET Core, można skonfigurować, jak projekt powinien być uruchamiany w scenariuszach rozwoju, dostosowując zawartość pliku launchSettings.json. W programie Visual Studio dla komputerów Mac można zaktualizować ten plik przy użyciu interfejsu użytkownika opcji projektu lub bezpośrednio edytując go. Ten plik jest tym samym plikiem konfiguracyjnym, którego można `dotnet`użyć podczas uruchamiania programu Visual Studio w systemie Windows lub z wiersza polecenia za pośrednictwem programu . Ten plik jest przechowywany w projekcie w folderze Właściwości.

Aby uzyskać bardziej szczegółowe informacje, zobacz [Używanie wielu środowisk w ASP.NET Core](/aspnet/core/fundamentals/environments). W tym artykule omówimy sposób aktualizowania tego pliku w programie Visual Studio dla komputerów Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Aktualizowanie konfiguracji startowej przy użyciu programu Visual Studio dla komputerów Mac

Można bezpośrednio edytować plik launchSettings.json w programie Visual Studio dla komputerów Mac lub użyć opcji projektu, aby go edytować. Aby przejść do opcji projektu, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Opcje**.

![Menu skrótów projektu z wybraną opcją "Opcje"](media/vsmac-ctx-proj-options.png)

Wybierz **pozycję Uruchom** > **domyślne konfiguracje** > **.**

!["Uruchom", "Konfiguracje" i "Domyślne" w opcjach projektu](media/vsmac-run-config-default.png)

Przede wszystkim w tym miejscu skonfigurujesz dwie rzeczy:

 - Zmienne środowiskowe
 - Adres URL aplikacji dla projektu

## <a name="configure-environment-variables"></a>Konfigurowanie zmiennych środowiskowych

Za pomocą siatki można określić wartości dla zmiennych środowiskowych. Te zmienne środowiskowe zostaną ustawione po uruchomieniu aplikacji w programie Visual Studio dla komputerów Mac. Podczas tworzenia aplikacji ASP.NET Core, należy pamiętać o specjalnej `ASPNETCORE_ENVIRONMENT` zmiennej środowiskowej. Aby dowiedzieć się więcej, zobacz [Używanie wielu środowisk w ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Konfigurowanie początkowego adresu URL

Aby skonfigurować adres URL, z który zostanie uruchomiona aplikacja, przejdź do **karty ASP.NET Core.**

![Adres URL aplikacji w opcjach projektu](media/vsmac-run-config-default-aspnetcore.png)

W tym miejscu można określić adres URL, który aplikacja będzie nasłuchiwać po uruchomieniu.