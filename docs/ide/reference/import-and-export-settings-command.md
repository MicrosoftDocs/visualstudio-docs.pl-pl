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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 409c0f40adfd374065dedb842965d2d1237bc9a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568831"
---
# <a name="import-and-export-settings-command"></a>Import i eksport ustawień — Polecenie

Importuje, eksportuje lub resetuje ustawienia programu Visual Studio.

## <a name="syntax"></a>Składnia

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Przełączniki

/Export:`filename`

Opcjonalny. Eksportuje bieżące ustawienia do określonego pliku.

/import:`filename`

Opcjonalny. Importuje ustawienia w określonym pliku.

/Reset

Opcjonalny. Resetuje bieżące ustawienia.

## <a name="remarks"></a>Uwagi

Uruchomienie tego polecenia bez przełączników powoduje otwarcie kreatora **importowania i eksportowania ustawień** . Aby uzyskać więcej informacji, zobacz [Synchronizowanie ustawień](../synchronized-settings-in-visual-studio.md) i [ustawień środowiska](../environment-settings.md).

## <a name="example"></a>Przykład

Następujące polecenie eksportuje bieżące ustawienia do pliku `MyFile.vssettings`:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Zobacz także

- [Ustawienia środowiska](../../ide/environment-settings.md)
- [Synchronizuj ustawienia](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md)
