---
title: Obsługa kodu launchSettings.json
description: Ten dokument obejmuje pomoc techniczną dotyczącą launchSettings.jsw programie Visual Studio dla komputerów Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: df702b5d49e5204e65675c1c57d222e490a33824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247931"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Podczas tworzenia projektów ASP.NET Core, można skonfigurować sposób uruchamiania projektu w scenariuszach programistycznych przez dostosowanie zawartości launchSettings.jsna pliku. W Visual Studio dla komputerów Mac można zaktualizować ten plik za pomocą interfejsu użytkownika opcji projektu lub przez bezpośrednie edytowanie go. Ten plik jest tym samym plikiem konfiguracji, którego można użyć podczas uruchamiania programu Visual Studio w systemie Windows lub za pomocą polecenia `dotnet` . Ten plik jest przechowywany w projekcie w folderze właściwości.

Aby uzyskać bardziej szczegółowe informacje, zobacz [Używanie wielu środowisk w ASP.NET Core](/aspnet/core/fundamentals/environments). W tym artykule omówiono sposób aktualizowania tego pliku w Visual Studio dla komputerów Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Zaktualizuj konfigurację początkową za pomocą Visual Studio dla komputerów Mac

launchSettings.jsmożna edytować bezpośrednio w pliku Visual Studio dla komputerów Mac lub użyć opcji projektu, aby go edytować. Aby przejść do opcji projektu, kliknij prawym przyciskiem myszy projekt i wybierz **Opcje**.

![Menu skrótów projektu z wybraną opcją "Opcje"](media/vsmac-ctx-proj-options.png)

Wybierz pozycję **Uruchom**  >  **konfiguracje**  >  **domyślne**.

!["Run", "konfiguracje" i "domyślne" w opcjach projektu](media/vsmac-run-config-default.png)

Przede wszystkim skonfigurujesz dwie rzeczy tutaj:

- Zmienne środowiskowe
- Adres URL aplikacji dla projektu

## <a name="configure-environment-variables"></a>Konfigurowanie zmiennych środowiskowych

Możesz użyć siatki, aby określić wartości zmiennych środowiskowych. Te zmienne środowiskowe zostaną ustawione podczas uruchamiania aplikacji w Visual Studio dla komputerów Mac. Podczas tworzenia aplikacji ASP.NET Core należy pamiętać o specjalnej `ASPNETCORE_ENVIRONMENT` zmiennej środowiskowej. Aby dowiedzieć się więcej, zobacz [Używanie wielu środowisk w ASP.NET Core](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Skonfiguruj początkowy adres URL

Aby skonfigurować adres URL, za pomocą którego zostanie uruchomiona aplikacja, przejdź do karty **ASP.NET Core** .

![Adres URL aplikacji w opcjach projektu](media/vsmac-run-config-default-aspnetcore.png)

W tym miejscu możesz określić adres URL, na którym aplikacja będzie nasłuchiwał, gdy zostanie uruchomiona.
