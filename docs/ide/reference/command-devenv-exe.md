---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 434b2ad0f2a6ca4d84c6d82bf9a1a85876a4d975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570404"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Wykonuje określone polecenie po uruchomieniu środowiska IDE programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Argumenty

*Commandname*

Wymagany. Pełna nazwa polecenia programu Visual Studio lub jego aliasu, ujęta w cudzysłów podwójnych. Aby uzyskać więcej informacji na temat składni poleceń i aliasów, zobacz [Polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Uwagi

Po zakończeniu uruchamiania IDE wykonuje nazwane polecenie.

::: moniker range="vs-2017"

Jeśli używasz tego przełącznika, IDE nie wyświetla strony początkowej podczas uruchamiania.

::: moniker-end

Jeśli dodatek udostępnia polecenie, można użyć tego przełącznika, aby uruchomić dodatek z wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Jak: Sterowanie dodatkami za pomocą menedżera dodatków](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Przykład

W pierwszym przykładzie uruchamia program Visual Studio i automatycznie uruchamia makro Otwórz ulubione pliki.

Drugi przykład otwiera kartę przeglądania sieci Web w środowisku IDE i przechodzi do witryny Microsoft Docs.

Trzeci przykład tworzy nowy `some_file.cs` plik o nazwie i otwiera go w edytorze kodu.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Okno polecenia](command-window.md)
