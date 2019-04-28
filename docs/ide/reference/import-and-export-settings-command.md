---
title: Import i eksport ustawień — Polecenie
ms.date: 11/21/2018
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
ms.openlocfilehash: b9be5826edf0d7220d30ce5c4a99f333c2ab8b67
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953221"
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