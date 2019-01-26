---
title: Import i eksport ustawień — Polecenie
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5c011c1bbaaa66e3da39c7ca8d713099d11e5a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041688"
---
# <a name="import-and-export-settings-command"></a>Import i eksport ustawień — Polecenie

Importuje, eksportuje lub resetuje ustawienia programu Visual Studio.

## <a name="syntax"></a>Składnia

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Przełączniki

/ export:`filename`

Opcjonalna. Eksportuje bieżące ustawienia do określonego pliku.

Import:`filename`

Opcjonalna. Importuje ustawienia w określonym pliku.

/reset

Opcjonalna. Przywraca bieżące ustawienia.

## <a name="remarks"></a>Uwagi

Uruchomienie tego polecenia, na których nie zmienia otwiera **Import i eksport ustawień** kreatora. Aby uzyskać więcej informacji, zobacz [synchronizację ustawień](../synchronized-settings-in-visual-studio.md) i [ustawienia środowiska](../environment-settings.md).

## <a name="example"></a>Przykład

Następujące polecenie eksportuje bieżące ustawienia do pliku `MyFile.vssettings`:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Zobacz także

- [Ustawienia środowiska](../../ide/environment-settings.md)
- [Synchronizowanie ustawień](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md)