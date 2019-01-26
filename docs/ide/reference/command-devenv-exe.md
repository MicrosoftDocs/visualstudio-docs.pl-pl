---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65c9533a12b8c3f5cd163889315c613b65ff6523
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002590"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Wykonuje określone polecenie po uruchomieniu programu Visual Studio IDE.

## <a name="syntax"></a>Składnia

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Argumenty

- *commandName*

  Wymagana. Pełna nazwa polecenia programu Visual Studio lub jego alias, ujęte w podwójny cudzysłów. Aby uzyskać więcej informacji o syntaksie aliasów i poleceń, zobacz [polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Uwagi

Po zakończeniu uruchamiania, IDE wykonuje polecenie nazwane. Jeśli używasz tego przełącznika, IDE nie wyświetla Visual Studio strony początkowej podczas uruchamiania.

Jeśli dodatek udostępnia polecenia, można użyć tego przełącznika, aby uruchomić dodatek z wiersza polecenia. Aby uzyskać więcej informacji, zobacz [jak: Kontrolowanie dodatków za pomocą Menedżera dodatków](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Przykład

Pierwszy przykład uruchamia programu Visual Studio i automatycznie uruchamia makro otwierania ulubionych plików.

Drugi przykład otwiera sieci web, przeglądanie karty w środowisku IDE i przechodzi do witryny Microsoft Docs.

Trzeci przykład tworzy nowy plik o nazwie `some_file.cs` i otwiera go w edytorze kodu.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Okno polecenia](command-window.md)