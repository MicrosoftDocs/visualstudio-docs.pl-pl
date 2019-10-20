---
title: -ResetSettings (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41e402a9268acecb70c83e26bab0e682d4ec59f5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665583"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przywraca domyślne ustawienia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i automatycznie uruchamia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Opcjonalnie resetuje ustawienia do określonego pliku. vssettings.

 Ustawienia domyślne są określane przez profil, który został wybrany podczas pierwszego uruchomienia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Składnia

```
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argumenty
 `SettingsFile` pełną ścieżkę i nazwę pliku. vssettings, który ma zostać zastosowany do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

 Aby przywrócić profil ogólnych ustawień deweloperskich, użyj `General`.

## <a name="remarks"></a>Uwagi
 Jeśli `SettingsFile` nie zostanie określona, zostanie wyświetlony monit o wybranie domyślnej kolekcji ustawień przy następnym uruchomieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="example"></a>Przykład
 Poniższy wiersz polecenia stosuje ustawienia przechowywane w pliku `MySettings.vssettings`.

```
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md)
