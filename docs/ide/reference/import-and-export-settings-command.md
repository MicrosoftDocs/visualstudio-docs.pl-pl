---
description: Importuje, eksportuje lub resetuje Visual Studio danych. Rozszerzenie pliku vssettings
title: Import i eksport ustawień — Polecenie
ms.date: 05/28/2021
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
ms.openlocfilehash: dba50cf598c3c74f6c9407fbef5d55f938941a11
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687636"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Polecenie Importuj i Eksportuj ustawienia (plik vssettings)

Importuje, eksportuje lub resetuje Visual Studio ustawień, `.vssettings` .

Schemat pliku jest otwarty. Najczęściej schemat jest zgodny ze strukturą XML, w której każda kategoria jest tagiem, który sam może zawierać tagi podkategorii. Tagi podkategorii mogą zawierać tagi wartości właściwości. Chociaż większość pakietów używa wspólnej struktury, każdy pakiet w Visual Studio może współtwolić dowolny kod XML do pliku przy użyciu schematu, który wybierze.

## <a name="syntax"></a>Składnia

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Przełączniki

/export:`filename`

Opcjonalny. Eksportuje bieżące ustawienia do określonego pliku.

/import:`filename`

Opcjonalny. Importuje ustawienia w określonym pliku.

/reset

Opcjonalny. Resetuje bieżące ustawienia.

## <a name="remarks"></a>Uwagi

Uruchomienie tego polecenia bez przełączników powoduje otwarcie **Kreatora importowania i eksportowania** ustawień. Aby uzyskać więcej informacji, zobacz [Synchronize your settings (Synchronizowanie ustawień)](../synchronized-settings-in-visual-studio.md) [i Environment settings (Ustawienia środowiska).](../environment-settings.md)

## <a name="example"></a>Przykład

Następujące polecenie eksportuje bieżące ustawienia do pliku `MyFile.vssettings` :

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```



## <a name="see-also"></a>Zobacz też

- [Ustawienia środowiska](../../ide/environment-settings.md)
- [Synchronizowanie ustawień](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizowanie Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
