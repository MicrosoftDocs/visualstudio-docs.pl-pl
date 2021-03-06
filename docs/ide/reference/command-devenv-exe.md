---
title: -Command (devenv.exe)
description: Dowiedz się, jak za pomocą przełącznika wiersza polecenia devenv wykonać określone polecenie po uruchomieniu środowiska IDE programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38738dad275b38fe0c5a6a70104e80f6a794bab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882189"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Wykonuje określone polecenie po uruchomieniu środowiska IDE programu Visual Studio.

## <a name="syntax"></a>Składnia

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Argumenty

*CommandName*

Wymagane. Pełna nazwa polecenia programu Visual Studio lub jego alias ujęty w znaki podwójnego cudzysłowu. Aby uzyskać więcej informacji na temat składni poleceń i aliasów, zobacz [Visual Studio Commands](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Uwagi

Po zakończeniu uruchamiania środowisko IDE wykonuje nazwane polecenie.

::: moniker range="vs-2017"

Jeśli używasz tego przełącznika, IDE nie wyświetla strony początkowej przy uruchamianiu.

::: moniker-end

Jeśli dodatek uwidacznia polecenie, można użyć tego przełącznika, aby uruchomić dodatek z wiersza polecenia. Aby uzyskać więcej informacji, zobacz [jak: kontrolowanie dodatków za pomocą Menedżera dodatków](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Przykład

Pierwszy przykład uruchamia program Visual Studio i automatycznie uruchamia makro Otwórz Ulubione pliki.

Drugi przykład otwiera kartę przeglądanie sieci Web w środowisku IDE i przechodzi do witryny Microsoft Docs.

Trzeci przykład tworzy nowy plik o nazwie `some_file.cs` i otwiera go w edytorze kodu.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Okno polecenia](command-window.md)
