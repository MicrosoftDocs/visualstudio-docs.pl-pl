---
title: Obsługa profilu launchsettings. JSON
description: W tym dokumencie opisano obsługę profilu launchsettings. JSON w Visual Studio dla komputerów Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: e7de368dd26bf2724a7bc060dade46422817da1e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213760"
---
# <a name="launchsettingsjson"></a>Profilu launchsettings. JSON

Podczas tworzenia projektów ASP.NET Core można skonfigurować sposób uruchamiania projektu w scenariuszach programistycznych przez dostosowanie zawartości `launchSettings.json` pliku. W Visual Studio dla komputerów Mac można zaktualizować ten plik za pomocą interfejsu użytkownika opcji projektu lub bezpośrednio edytując `launchSettings.json` plik. Ten plik jest tym samym plikiem konfiguracji, który może być używany podczas uruchamiania programu Visual Studio w systemie Windows lub za pomocą `dotnet`polecenia. Ten plik jest przechowywany w projekcie `Properties` w folderze.

Więcej szczegółowych informacji można znaleźć [w temacie Używanie wielu środowisk w ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). W tym dokumencie omówiono sposób aktualizowania tego pliku w Visual Studio dla komputerów Mac.

## <a name="updating-start-configuration-using-visual-studio-for-mac"></a>Aktualizowanie konfiguracji początkowej przy użyciu Visual Studio dla komputerów Mac

Możesz bezpośrednio edytować `launchSettings.json` w Visual Studio dla komputerów Mac lub użyć opcji projektu, aby go edytować. Aby przejść do opcji projektu, kliknij prawym przyciskiem myszy projekt i wybierz opcje. Zapoznaj się z poniższym obrazem.

![wybrane opcje menu kontekstowego projektu](media/vsmac-ctx-proj-options.png)

Po wyświetleniu tego okna dialogowego wybierz kolejno pozycje Uruchom Konfiguracje > > domyślne.

![Uruchom domyślne konfiguracje](media/vsmac-run-config-default.png)

Istnieją głównie dwie elementy, które można skonfigurować w tym miejscu.

 - Zmienne środowiskowe ustawione w menu Start
 - Początkowy adres URL projektu

## <a name="configure-environment-variables"></a>Konfigurowanie zmiennych środowiskowych

Możesz użyć siatki, aby określić wartości zmiennych środowiskowych. Te zmienne środowiskowe zostaną ustawione podczas uruchamiania aplikacji w Visual Studio dla komputerów Mac. Podczas tworzenia aplikacji ASP.NET Core należy pamiętać o specjalnej `ASPNETCORE_ENVIRONMENT` zmiennej środowiskowej. Aby dowiedzieć się więcej, zobacz [Używanie wielu środowisk w ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-start-url"></a>Skonfiguruj początkowy adres URL

Aby skonfigurować adres URL, za pomocą którego aplikacja zostanie uruchomiona, przejdź do karty ASP.NET Core.

![początkowy adres URL opcji proj](media/vsmac-run-config-default-aspnetcore.png)

W tym miejscu możesz określić adresy URL, na których będzie nasłuchiwać aplikacja, gdy zostanie ona uruchomiona.