---
title: -ResetSettings (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3549801001ba8df60634884dc58137a8fa77d905
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655564"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Przywraca ustawienia domyślne programu Visual Studio i automatycznie uruchamia środowisko IDE programu Visual Studio. Ten przełącznik opcjonalnie resetuje ustawienia do określonego pliku ustawień.

Ustawienia domyślne pochodzą z profilu, który został wybrany podczas pierwszego uruchomienia programu Visual Studio.

> [!TIP]
> Aby dowiedzieć się, jak zresetować ustawienia przy użyciu zintegrowanego środowiska programistycznego (IDE), zobacz [Resetowanie ustawień](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Składnia

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Argumenty

- *SettingsFile*

  Opcjonalny. Pełna ścieżka i nazwa pliku ustawień, który ma zostać zastosowany do programu Visual Studio.

- *DefaultCollectionSpecifier*

  Opcjonalny. Specyfikator reprezentujący domyślną kolekcję ustawień do przywrócenia. Wybierz jeden z domyślnych specyfikatorów kolekcji wymienionych w tabeli.

  | Domyślna nazwa kolekcji | Specyfikator kolekcji |
  | --- | --- |
  | **Ogólne** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Programowanie dla sieci Web** | `Web` |
  | **Programowanie dla sieci Web (tylko kod)** | `WebCode` |

## <a name="remarks"></a>Uwagi

Jeśli *SettingsFile* nie zostanie określony, IDE zostanie otwarty przy użyciu istniejących ustawień.

## <a name="example"></a>Przykład

Pierwszy przykład stosuje ustawienia przechowywane w pliku `MySettings.vssettings`.

Drugi przykład przywraca domyślny profil wizualizacji C# .

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Zobacz także

- [Ustawienia środowiska](../environment-settings.md)
- [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)