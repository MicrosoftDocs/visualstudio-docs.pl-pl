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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0be61d8690c0605f6e7773efe02f5db351110f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658777"
---
# <a name="import-and-export-settings-command"></a>Import i eksport ustawień — Polecenie

Importuje, eksportuje lub resetuje ustawienia programu Visual Studio.

## <a name="syntax"></a>Składnia

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Przełączniki

/Export: `filename`

Opcjonalny. Eksportuje bieżące ustawienia do określonego pliku.

/import: `filename`

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
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)