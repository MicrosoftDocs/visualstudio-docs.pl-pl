---
title: Przykładowe parametry wiersza polecenia do zainstalowania
description: Dostosuj te przykłady do tworzenia własnych instalacji z wiersza polecenia programu Visual Studio.
ms.date: 01/15/2019
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59dfe6ebb9518bbdea6edf11108f1cb27cd5d6a3
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345529"
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Przykładowe parametry wiersza polecenia dla instalacji programu Visual Studio 2017

Aby zilustrować, jak [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md), poniżej przedstawiono kilka przykładów, które można dostosować do potrzeb.

W każdym przykładzie `vs_enterprise.exe`, `vs_professional.exe` i `vs_community.exe` reprezentują odpowiedniej wersji program inicjujący programu Visual Studio, czyli pliku małe (około 1 MB), który inicjuje proces pobierania. Jeśli używasz innej wersji, należy zastąpić nazwę odpowiedniego programu inicjującego.

> [!NOTE]
> Wszystkie polecenia wymaga podniesienia uprawnień administracyjnych oraz Kontrola konta użytkownika, jeśli proces nie jest uruchomiona w wierszu polecenia z podwyższonym poziomem uprawnień zostanie wyświetlony monit.
>
> [!NOTE]
> Możesz użyć `^` znak na końcu wiersza polecenia do łączenia wielu wierszy w pojedynczym poleceniu. Alternatywnie można po prostu umieścić te wiersze razem na jeden wiersz. W programie PowerShell odpowiednik to początkowych (`` ` ``) znaków.

## <a name="using---installpath"></a>Przy użyciu opcji--installPath

* Zainstaluj minimalny wystąpienia programu Visual Studio przy użyciu nie interaktywne monity, ale wyświetlany postęp:

  ```cmd
  vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Aktualizacja wystąpienia programu Visual Studio przy użyciu wiersza polecenia nie interaktywne monity, ale wyświetlany postęp:

  ```cmd
  vs_enterprise.exe --update --quiet --wait
  vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
  ```

  > [!NOTE]
  > Oba polecenia są wymagane. Pierwsze polecenie aktualizuje Instalatora programu Visual Studio. Drugie polecenie aktualizuje wystąpienia programu Visual Studio. Aby uniknąć okno Kontrola konta użytkownika, należy uruchomić wiersz polecenia jako Administrator.

* Zainstalować pulpitu wystąpienia programu Visual Studio w trybie dyskretnym, przy użyciu pakietu języka francuskiego, zwracając tylko wtedy, gdy produkt jest zainstalowany.

  ```cmd
  vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

  > [!NOTE]
  > `--wait` Parametr jest przeznaczony do użytku w pliku wsadowym. Wykonanie następnego polecenia w pliku wsadowym, nie będzie kontynuowane, dopóki instalacja została ukończona. `%ERRORLEVEL%` Zmienna środowiskowa będzie zawierać wartość zwracaną przez polecenie, zgodnie z opisem w [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

## <a name="using---layout"></a>Przy użyciu opcji--układu

* Pobierz podstawowy edytor programu Visual Studio (najbardziej minimalny konfiguracji programu Visual Studio). Tylko obejmują pakiet języka angielskiego:

  ```cmd
  vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Pobierz .NET dla komputerów stacjonarnych i obciążenia sieci web platformy .NET oraz wszystkie zalecane składniki i rozszerzenia usługi GitHub. Tylko obejmują pakiet języka angielskiego:

  ```cmd
  vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Przy użyciu opcji--wszystko

* Rozpocznij instalacji interakcyjnej wszystkich obciążeń i składników, które są dostępne w wersji programu Visual Studio 2017 Enterprise:

  ```cmd
  vs_enterprise.exe --all
  ```

## <a name="using---includerecommended"></a>Za pomocą--includeRecommended

* Drugi nazwane wystąpienie programu Visual Studio 2017 Professional zostaną zainstalowane na komputerze z zainstalowanym, obsługę tworzenia aplikacji Node.js w wersji Visual Studio 2017 Community:

  ```cmd
  vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Przy użyciu opcji--Usuń

* Usuń składnik Profiling Tools z domyślnego zainstalowane wystąpienia programu Visual Studio:

  ```cmd
  vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

## <a name="using---path"></a>Przy użyciu opcji--ścieżki

Te parametry wiersza polecenia jest **Nowość w wersji 15.7**. Aby uzyskać więcej informacji na temat ich zobacz [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

* Korzystanie z instalacji, pamięci podręcznej i udostępnionej ścieżki:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Przy użyciu tylko ścieżki instalacji i pamięci podręcznej:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Przy użyciu tylko instalacji i udostępnionej ścieżki:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Przy użyciu tylko ścieżki instalacji:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Użycie opcji eksportowania

To polecenie wiersza polecenia jest **nowego w programie 15.9**. Aby uzyskać więcej informacji na ten temat, zobacz [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

* Użycie opcji eksportowania zapisać je przy użyciu instalacji:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
```

* Zapisz niestandardowy wybór od podstaw przy użyciu eksportu:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
```

## <a name="using---config"></a>Za pomocą--config

Ten parametr wiersza polecenia jest **nowego w programie 15.9**. Aby uzyskać więcej informacji na ten temat, zobacz [użyć parametrów wiersza polecenia, aby zainstalować program Visual Studio](use-command-line-parameters-to-install-visual-studio.md) strony.

* Do zainstalowania obciążeń i składników z pliku konfiguracji instalacji wcześniej zapisany, przy użyciu--config:

```cmd
vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
```

* Dodawanie obciążeń i składników do istniejącej instalacji przy użyciu--config:

```cmd
vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
```


[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tworzenie instalacji offline programu Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
