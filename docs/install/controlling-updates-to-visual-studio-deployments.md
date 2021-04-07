---
title: Sterowanie aktualizacjami wdrożeń
description: Dowiedz się, jak zmienić lokalizację, w której program Visual Studio poszukuje aktualizacji podczas instalacji z sieci.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8360c48e9868f6ed5d81fffc748d050404211228
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547495"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci

Administratorzy przedsiębiorstwa często tworzą układ i obsługują go w sieciowym udziale plików, aby wdrażać je dla użytkowników końcowych. Na tej stronie opisano, jak prawidłowo skonfigurować opcje układu sieciowego. 

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Kontrolowanie miejsca, w którym program Visual Studio szuka aktualizacji

**Scenariusz 1: klient pierwotnie zainstalowany z układu, ale jest skonfigurowany do otrzymywania aktualizacji z lokalizacji układu sieciowego lub sieci Web**

Domyślnie program Visual Studio kontynuuje wyszukiwanie aktualizacji nawet wtedy, gdy instalacja została pierwotnie wdrożona z udziału sieciowego. Jeśli w sieci Web jest dostępna aktualizacja, użytkownik może ją zainstalować. Mimo że pamięć podręczna układu sieciowego jest najpierw sprawdzana pod kątem wszelkich zaktualizowanych bitów produktu, jeśli nie zostały one tam odnalezione, program Visual Studio wyświetli i pobierze zaktualizowane bity produktu z sieci Web.

**Scenariusz 2: klient zainstalowany pierwotnie i powinien otrzymywać tylko aktualizacje z układu sieciowego**

Jeśli chcesz kontrolować miejsce, w którym klient programu Visual Studio szuka aktualizacji, na przykład jeśli komputer kliencki nie ma dostępu do Internetu i chcesz się upewnić, że tylko i zawsze jest instalowany z układu, można skonfigurować lokalizację, w której instalator klienta szuka zaktualizowanych bitów produktu. Najlepszym rozwiązaniem jest upewnienie się, że to ustawienie jest skonfigurowane poprawnie przed rozpoczęciem instalacji początkowej z układu przez klienta. 

1. Utwórz układ offline:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Skopiuj go do udziału plików, w którym chcesz go hostować:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Zmodyfikuj `response.json` plik w układzie i Zmień `channelUri` wartość tak, aby wskazywała kopię channelManifest.jsna tym formancie administratora.

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

2. Upewnij się, że `response.json` plik w zaktualizowanym układzie nadal zawiera dostosowania, w tym modyfikacje identyfikator channeluri, w następujący sposób:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

Istniejące instalacje programu Visual Studio z tego układu odszukają aktualizacje pod adresem `\\server\share\VS\ChannelManifest.json` . Jeśli channelManifest.jsw wersji nowszej niż zainstalowana przez użytkownika, program Visual Studio powiadamia użytkownika, że aktualizacja jest dostępna.

Każda aktualizacja instalacji zainicjowana z poziomu klienta automatycznie zainstaluje zaktualizowaną wersję programu Visual Studio bezpośrednio z układu.

**Scenariusz 3: klient pierwotnie zainstalowany z sieci Web, ale teraz powinien otrzymywać tylko aktualizacje z układu sieciowego**

W niektórych przypadkach na komputerze klienckim mógł już zostać zainstalowany program Visual Studio z sieci Web, ale teraz administrator chce, aby wszystkie przyszłe aktualizacje były dostarczane z zarządzanego układu. Jedynym obsługiwanym sposobem jest utworzenie układu sieciowego z odpowiednią wersją produktu, a następnie na komputerze klienckim uruchomienie programu inicjującego _z lokalizacji układu_ (np. `\\network\share\vs_enterprise.exe` ). W idealnym przypadku oryginalna instalacja klienta mogłaby nastąpić przy użyciu programu inicjującego z układu sieciowego ze skonfigurowanym prawidłowo identyfikator channeluri, ale uruchomienie zaktualizowanego programu inicjującego z lokalizacji układu sieciowego również będzie działać. Jedna z tych akcji zostałaby osadzona na komputerze klienckim, a połączenie z tą konkretną lokalizacją układu. Jedynym warunkiem, aby ten scenariusz działał prawidłowo, jest to, że "Identyfikator channeluri" w `response.json` pliku układu musi być taki sam jak identyfikator channeluri, który został ustawiony na komputerze klienta po wystąpieniu oryginalnej instalacji. Najprawdopodobniej ta wartość została pierwotnie ustawiona na [kanał wydania](https://aka.ms/vs/16/release/channel)internetowego. 


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

* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Włączanie aktualizacji administratorów](enabling-administrator-updates.md)
* [Stosowanie aktualizacji administratorów](applying-administrator-updates.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do zarządzania wystąpieniami programu Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
