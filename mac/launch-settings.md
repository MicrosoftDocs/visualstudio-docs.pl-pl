---
title: Obsługa profilu launchsettings. JSON
description: W tym dokumencie opisano obsługę profilu launchsettings. JSON w Visual Studio dla komputerów Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: 7135dd05c687e3caed3ee64618ff71c093f4cd63
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322580"
---
# <a name="launchsettingsjson"></a>Profilu launchsettings. JSON

Podczas tworzenia projektów ASP.NET Core, można skonfigurować sposób uruchamiania projektu w scenariuszach programistycznych przez dostosowanie zawartości pliku profilu launchsettings. JSON. W Visual Studio dla komputerów Mac można zaktualizować ten plik za pomocą interfejsu użytkownika opcji projektu lub przez bezpośrednie edytowanie go. Ten plik jest tym samym plikiem konfiguracji, którego można użyć podczas uruchamiania programu Visual Studio w systemie Windows lub za pomocą `dotnet`polecenia. Ten plik jest przechowywany w projekcie w folderze właściwości.

Aby uzyskać bardziej szczegółowe informacje, zobacz [Używanie wielu środowisk w ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). W tym artykule omówiono sposób aktualizowania tego pliku w Visual Studio dla komputerów Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Zaktualizuj konfigurację początkową za pomocą Visual Studio dla komputerów Mac

Plik profilu launchsettings. JSON można edytować bezpośrednio w Visual Studio dla komputerów Mac lub można użyć opcji projektu, aby go edytować. Aby przejść do opcji projektu, kliknij prawym przyciskiem myszy projekt i wybierz **Opcje**.

![Menu skrótów projektu z wybraną opcją "Opcje"](media/vsmac-ctx-proj-options.png)

Wybierz pozycję **Uruchom** > **konfiguracje** > **domyślne**.

!["Run", "konfiguracje" i "domyślne" w opcjach projektu](media/vsmac-run-config-default.png)

Przede wszystkim skonfigurujesz dwie rzeczy tutaj:

 - Zmienne środowiskowe
 - Adres URL aplikacji dla projektu

## <a name="configure-environment-variables"></a>Konfigurowanie zmiennych środowiskowych

Możesz użyć siatki, aby określić wartości zmiennych środowiskowych. Te zmienne środowiskowe zostaną ustawione podczas uruchamiania aplikacji w Visual Studio dla komputerów Mac. Podczas tworzenia aplikacji ASP.NET Core należy pamiętać o specjalnej `ASPNETCORE_ENVIRONMENT` zmiennej środowiskowej. Aby dowiedzieć się więcej, zobacz [Używanie wielu środowisk w ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Skonfiguruj początkowy adres URL

Aby skonfigurować adres URL, za pomocą którego zostanie uruchomiona aplikacja, przejdź do karty **ASP.NET Core** .

![Adres URL aplikacji w opcjach projektu](media/vsmac-run-config-default-aspnetcore.png)

W tym miejscu możesz określić adres URL, na którym aplikacja będzie nasłuchiwał, gdy zostanie uruchomiona.