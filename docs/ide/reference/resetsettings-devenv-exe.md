---
title: -ResetSettings (devenv.exe)
description: Dowiedz się, jak za pomocą przełącznika wiersza polecenia ResetSettings devenv przywrócić domyślne ustawienia Visual Studio i automatycznie uruchamiać Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e523738ff23b40c80b5df21d90b582d94c59087f
ms.sourcegitcommit: a8031c1387d2090129ed33e063744f9f31653dcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2021
ms.locfileid: "110724541"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Przywraca Visual Studio domyślne i automatycznie uruchamia Visual Studio IDE. Ten przełącznik opcjonalnie resetuje ustawienia do określonego pliku ustawień ( `*.vssettings` ).

Ustawienia domyślne pochodzą z profilu wybranego podczas pierwszego Visual Studio aplikacji.

> [!TIP]
> Aby dowiedzieć się, jak resetować ustawienia przy użyciu zintegrowanego środowiska projektowego (IDE), zobacz [Resetowanie ustawień](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Składnia

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Argumenty

- *SettingsFile*

  Opcjonalny. Pełna ścieżka i nazwa `.vssettings` pliku, który ma być Visual Studio.

- *DefaultCollectionSpecifier*

  Opcjonalny. Specyfikator reprezentujący domyślną kolekcję ustawień do przywrócenia. Wybierz jeden z domyślnych specyfikatorów kolekcji wymienionych w tabeli.

  | Domyślna nazwa kolekcji | Specyfikator kolekcji |
  | --- | --- |
  | **Ogólne** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C #** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Programowanie dla sieci Web** | `Web` |
  | **Tworzenie aplikacji internetowych (tylko kod)** | `WebCode` |

## <a name="remarks"></a>Uwagi

Jeśli nie *określono ustawieniapliku,* zostanie otwarte ide przy użyciu istniejących ustawień. 


## <a name="example"></a>Przykład

Pierwszy przykład dotyczy ustawień przechowywanych w pliku `MySettings.vssettings` .

Drugi przykład przywraca domyślny profil języka Visual C#.

Trzeci przykład spowoduje również zamknięcie Visual Studio po zastosowaniu ustawień. Możesz dołączyć `/Command "File.Exit"` .

```shell
devenv /ResetSettings "%USERPROFILE%\MySettings.vssettings"

devenv /ResetSettings CSharp

devenv /NoSplash /ResetSettings General /Command Exit 
```

## <a name="see-also"></a>Zobacz też

- [Ustawienia środowiska](../environment-settings.md)
- [Personalizowanie Visual Studio IDE](../../ide/personalizing-the-visual-studio-ide.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
