---
description: Importuje, eksportuje lub resetuje ustawienia programu Visual Studio.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f2ea4811af2c44277b9a6dc285972c5267b28d7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223679"
---
# <a name="import-and-export-settings-command"></a>Import i eksport ustawień — Polecenie

Importuje, eksportuje lub resetuje ustawienia programu Visual Studio.

## <a name="syntax"></a>Składnia

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Przełączniki

/Export`filename`

Opcjonalny. Eksportuje bieżące ustawienia do określonego pliku.

/import`filename`

Opcjonalny. Importuje ustawienia w określonym pliku.

/Reset

Opcjonalny. Resetuje bieżące ustawienia.

## <a name="remarks"></a>Uwagi

Uruchomienie tego polecenia bez przełączników powoduje otwarcie kreatora **importowania i eksportowania ustawień** . Aby uzyskać więcej informacji, zobacz [Synchronizowanie ustawień](../synchronized-settings-in-visual-studio.md) i [ustawień środowiska](../environment-settings.md).

## <a name="example"></a>Przykład

Następujące polecenie eksportuje bieżące ustawienia do pliku `MyFile.vssettings` :

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Zobacz też

- [Ustawienia środowiska](../../ide/environment-settings.md)
- [Synchronizuj ustawienia](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
