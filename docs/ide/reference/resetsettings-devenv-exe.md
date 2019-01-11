---
title: -ResetSettings (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52c3576b10fdc88563b3689e4b37d71b7f4659cd
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227554"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Przywraca ustawienia domyślne programu Visual Studio i automatycznie uruchamia IDE programu Visual Studio. Ten przełącznik opcjonalnie resetuje ustawienia do pliku określonego ustawienia.

Domyślne ustawienia pochodzą z profilu, który został wybrany, gdy program Visual Studio najpierw została uruchomiona.

> [!TIP]
> Aby dowiedzieć się, jak zresetować ustawienia za pomocą zintegrowanego środowiska programistycznego (IDE), zobacz [zresetować ustawienia](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Składnia

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Argumenty

- *Plik_ustawień*

  Opcjonalna. Pełna ścieżka i nazwa pliku ustawień do zastosowania w programie Visual Studio.

- *DefaultCollectionSpecifier*

  Opcjonalna. Specyfikatora, reprezentujący domyślną kolekcję ustawień do przywrócenia. Wybierz jedną z specyfikatory kolekcji domyślne, które są wymienione w tabeli.

  | Domyślna nazwa kolekcji | Specyfikator kolekcji |
  | --- | --- |
  | **Ogólne** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Tworzenie aplikacji sieci Web** | `Web` |
  | **Tworzenie aplikacji sieci Web (tylko kod)** | `WebCode` |

## <a name="remarks"></a>Uwagi

Jeśli nie *Plik_ustawień* jest określony, IDE otwiera przy użyciu istniejących ustawień.

## <a name="example"></a>Przykład

Pierwszy przykład zastosowanie ustawień przechowywanych w pliku `MySettings.vssettings`.

Drugi przykład przywraca wizualizacji C# profil domyślny.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Zobacz także

- [Ustawienia środowiska](../environment-settings.md)
- [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)