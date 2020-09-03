---
title: Sterowanie aktualizacjami wdrożeń
description: Dowiedz się, jak zmienić lokalizację, w której program Visual Studio poszukuje aktualizacji podczas instalacji z sieci.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8743f042c7c33da34895f93e5df3990f6e0b2ed2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115310"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci

Administratorzy przedsiębiorstwa często tworzą układ i obsługują go w sieciowym udziale plików, aby wdrażać je dla użytkowników końcowych.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Kontrolowanie miejsca, w którym program Visual Studio szuka aktualizacji

Domyślnie program Visual Studio nadal wyszukuje aktualizacje w trybie online, nawet jeśli instalacja została wdrożona z udziału sieciowego. Jeśli dostępna jest aktualizacja, użytkownik może ją zainstalować. Zawartość, która nie została znaleziona w układzie offline, jest pobierana z sieci Web.

Jeśli chcesz mieć bezpośrednią kontrolę nad tym, gdzie program Visual Studio szuka aktualizacji, możesz zmodyfikować lokalizację, w której ma się pojawić. Możesz również kontrolować wersję, do której użytkownicy są aktualizowani. Aby to zrobić, wykonaj następujące kroki:

1. Utwórz układ offline:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Skopiuj go do udziału plików, w którym chcesz go hostować:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Zmodyfikuj response.jsw pliku w układzie i Zmień `channelUri` wartość tak, aby wskazywała kopię channelManifest.jsna tym formancie administratora.

   Upewnij się, że w wartości są wyprowadzane ukośniki odwrotne, jak w poniższym przykładzie:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Teraz użytkownicy końcowi mogą uruchomić Instalatora z tego udziału, aby zainstalować program Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Gdy administrator przedsiębiorstwa określi czas, aby użytkownicy mogli zaktualizować do nowszej wersji programu Visual Studio, mogą [zaktualizować lokalizację układu](update-a-network-installation-of-visual-studio.md) w celu uwzględnienia zaktualizowanych plików w następujący sposób.

1. Użyj polecenia, które jest podobne do następującego polecenia:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Upewnij się, że response.jsw pliku w zaktualizowanym układzie nadal zawiera dostosowania, w tym modyfikacje identyfikator channeluri, w następujący sposób:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Istniejące instalacje programu Visual Studio z tego układu odszukają aktualizacje pod adresem `\\server\share\VS\ChannelManifest.json` . Jeśli channelManifest.jsw wersji nowszej niż zainstalowana przez użytkownika, program Visual Studio powiadamia użytkownika, że aktualizacja jest dostępna.

   Nowe instalacje automatycznie instalują zaktualizowaną wersję programu Visual Studio bezpośrednio z układu.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Kontrolowanie powiadomień w środowisku IDE programu Visual Studio

::: moniker range="vs-2017"

Jak opisano wcześniej, program Visual Studio sprawdza lokalizację, z której została zainstalowana, na przykład udział sieciowy lub Internet, aby sprawdzić, czy są dostępne aktualizacje. Po udostępnieniu aktualizacji program Visual Studio powiadamia użytkownika z flagą powiadomienia w prawym górnym rogu okna.

   ![Flaga powiadomienia dla aktualizacji](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Jak opisano wcześniej, program Visual Studio sprawdza lokalizację, z której została zainstalowana, na przykład udział sieciowy lub Internet, aby sprawdzić, czy są dostępne aktualizacje. Po udostępnieniu aktualizacji program Visual Studio powiadamia użytkownika o ikonie powiadomienia w prawym dolnym rogu okna.

   ![Ikona powiadomienia w środowisku IDE programu Visual Studio](media/vs-2019/notification-bar.png "Ikona powiadomienia w środowisku IDE programu Visual Studio")

::: moniker-end

Powiadomienia można wyłączyć, jeśli nie chcesz, aby użytkownicy końcowi byli powiadamiani o aktualizacjach. (Na przykład może być konieczne wyłączenie powiadomień w przypadku dostarczania aktualizacji za pomocą centralnego mechanizmu dystrybucji oprogramowania).

::: moniker range="vs-2017"

Ponieważ program Visual Studio 2017 [przechowuje wpisy rejestru w rejestrze prywatnym](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nie można bezpośrednio edytować rejestru w typowy sposób. Program Visual Studio zawiera jednak `vsregedit.exe` narzędzie umożliwiające zmianę ustawień programu Visual Studio. Powiadomienia można wyłączyć za pomocą następującego polecenia:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Ponieważ program Visual Studio 2019 [przechowuje wpisy rejestru w rejestrze prywatnym](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nie można bezpośrednio edytować rejestru w typowy sposób. Program Visual Studio zawiera jednak `vsregedit.exe` narzędzie umożliwiające zmianę ustawień programu Visual Studio. Powiadomienia można wyłączyć za pomocą następującego polecenia:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Pamiętaj, aby zastąpić katalog, aby był zgodny z zainstalowanym wystąpieniem, które chcesz edytować).

> [!TIP]
> Użyj [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) , aby znaleźć określone wystąpienie programu Visual Studio na stacji roboczej klienta.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do zarządzania wystąpieniami programu Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
