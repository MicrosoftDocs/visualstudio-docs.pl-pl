---
title: Sterowanie aktualizacjami wdrożeń
description: Dowiedz się, jak zmienić sposób, w którym program Visual Studio szuka aktualizacji podczas instalacji z sieci.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115310"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci

Administratorzy przedsiębiorstwa często tworzą układ i hostują go w sieciowym udziale plików, aby wdrożyć go u swoich użytkowników końcowych.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Kontrolowanie, gdzie program Visual Studio szuka aktualizacji

Domyślnie program Visual Studio nadal szuka aktualizacji w trybie online, nawet jeśli instalacja została wdrożona z udziału sieciowego. Jeśli aktualizacja jest dostępna, użytkownik może ją zainstalować. Wszelkie zaktualizowane treści, których nie znaleziono w układzie trybu offline, są pobierane z sieci Web.

Jeśli chcesz mieć bezpośrednią kontrolę nad tym, gdzie program Visual Studio szuka aktualizacji, można zmodyfikować lokalizację, w której wygląda. Można również kontrolować wersję, do której użytkownicy są aktualizowani. Aby to zrobić, wykonaj następujące kroki:

1. Tworzenie układu trybu offline:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Skopiuj go do udziału plików w miejscu, w którym chcesz go hostować:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Zmodyfikuj plik response.json `channelUri` w układzie i zmień wartość, aby wskazać kopię kanałuManifest.json, który kontroluje administrator.

   Pamiętaj, aby uniknąć ukośników odwrotnych w wartości, jak w poniższym przykładzie:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Teraz użytkownicy końcowi mogą uruchamiać konfigurację z tego udziału, aby zainstalować program Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Gdy administrator przedsiębiorstwa stwierdzi, że nadszedł czas, aby ich użytkownicy zaktualizowali do nowszej wersji programu Visual Studio, mogą [zaktualizować lokalizację układu,](update-a-network-installation-of-visual-studio.md) aby uwzględnić zaktualizowane pliki, w następujący sposób.

1. Użyj polecenia podobnego do następującego polecenia:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Upewnij się, że plik response.json w zaktualizowanym układzie nadal zawiera dostosowania, w szczególności modyfikację channelUri, w następujący sposób:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Istniejące instalacje programu Visual Studio z `\\server\share\VS\ChannelManifest.json`tego układu poszukują aktualizacji w programie . Jeśli channelManifest.json jest nowsza niż zainstalowana przez użytkownika, program Visual Studio powiadamia użytkownika, że aktualizacja jest dostępna.

   Nowe instalacje automatycznie instalują zaktualizowaną wersję programu Visual Studio bezpośrednio z układu.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Kontrolowanie powiadomień w programie Visual Studio IDE

::: moniker range="vs-2017"

Jak opisano wcześniej, visual studio sprawdza lokalizację, z której został zainstalowany, takich jak udział sieciowy lub Internet, aby zobaczyć, czy są dostępne aktualizacje. Gdy aktualizacja jest dostępna, Visual Studio powiadamia użytkownika z flagą powiadomień w prawym górnym rogu okna.

   ![Flaga powiadomień o aktualizacjach](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Jak opisano wcześniej, visual studio sprawdza lokalizację, z której został zainstalowany, takich jak udział sieciowy lub Internet, aby zobaczyć, czy są dostępne aktualizacje. Gdy aktualizacja jest dostępna, Visual Studio powiadamia użytkownika z ikoną powiadomień w prawym dolnym rogu okna.

   ![Ikona powiadomienia w programie Visual Studio IDE](media/vs-2019/notification-bar.png "Ikona powiadomienia w programie Visual Studio IDE")

::: moniker-end

Możesz wyłączyć powiadomienia, jeśli nie chcesz, aby użytkownicy końcowi otrzymywać powiadomienia o aktualizacjach. (Na przykład można wyłączyć powiadomienia, jeśli dostarczasz aktualizacje za pośrednictwem centralnego mechanizmu dystrybucji oprogramowania).

::: moniker range="vs-2017"

Ponieważ program Visual Studio 2017 [przechowuje wpisy rejestru w rejestrze prywatnym,](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)nie można bezpośrednio edytować rejestru w typowy sposób. Jednak visual studio `vsregedit.exe` zawiera narzędzie, którego można użyć do zmiany ustawień programu Visual Studio. Powiadomienia można wyłączyć za pomocą następującego polecenia:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Ponieważ program Visual Studio 2019 [przechowuje wpisy rejestru w rejestrze prywatnym,](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)nie można bezpośrednio edytować rejestru w typowy sposób. Jednak visual studio `vsregedit.exe` zawiera narzędzie, którego można użyć do zmiany ustawień programu Visual Studio. Powiadomienia można wyłączyć za pomocą następującego polecenia:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Pamiętaj, aby zastąpić katalog, aby dopasować zainstalowane wystąpienie, które chcesz edytować).

> [!TIP]
> Użyj [vswhere.exe,](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) aby znaleźć określone wystąpienie programu Visual Studio na stacji roboczej klienta.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md)
* [Przewodnik dla administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do zarządzania wystąpieniami programu Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Cykl życia produktu i serwis programu Visual Studio](/visualstudio/releases/2019/servicing/)
