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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38144381520002e1e3e9f9c7b440d6b87b90cb6d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943330"
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

/ Reset

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