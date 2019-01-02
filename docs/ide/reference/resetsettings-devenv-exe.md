---
title: -ResetSettings (devenv.exe)
ms.date: 11/16/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 160cbf93cee8ff778a4f84ee833c7fac3d7f26b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830667"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Przywraca ustawienia domyślne programu Visual Studio i automatycznie uruchamia IDE programu Visual Studio. Opcjonalnie resetuje ustawienia do określonego *vssettings* pliku.

Ustawienia domyślne są określane przez profil, który został wybrany, gdy program Visual Studio najpierw została uruchomiona.

> [!TIP]
> Aby dowiedzieć się, jak zresetować ustawienia za pomocą zintegrowanego środowiska programistycznego (IDE), zobacz [zresetować ustawienia](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Składnia

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argumenty

`SettingsFile`

Pełna ścieżka i nazwa *vssettings* pliku, aby zastosować do programu Visual Studio.

Aby przywrócić profil ogólne ustawienia projektowe, użyj `General`.

## <a name="remarks"></a>Uwagi

Jeśli nie `SettingsFile` jest określona, zostanie wyświetlony monit o wybór domyślnej kolekcji ustawień przy następnym uruchomieniu programu Visual Studio.

## <a name="example"></a>Przykład

Następujący wiersz polecenia powoduje zastosowanie ustawień przechowywanych w pliku `MySettings.vssettings`.

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Zobacz także

- [Ustawienia środowiska](../environment-settings.md)
- [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)