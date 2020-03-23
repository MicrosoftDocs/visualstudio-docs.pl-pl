---
title: -LCID (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cabbf36adb5019543b3cfb72b0b0e56976517d2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557936"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Ustawia domyślny język używany dla tekstu, waluty i innych wartości w środowisku IDE.

## <a name="syntax"></a>Składnia

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argumenty

- *Localeid*

  Wymagany. Identyfikator ustawień regionalnych (LCID) określonego języka.

## <a name="remarks"></a>Uwagi

Ładuje IDE i ustawia domyślny język naturalny dla środowiska. Ta zmiana jest zachowywana między sesjami, a IDE pokazuje tę zmianę w**polu** Język**ustawień międzynarodowych** > **ustawień** > **Environment** > środowiska **narzędzi.** > 

Jeśli określony język nie jest dostępny w `/LCID` systemie, przełącznik jest ignorowany.

W poniższej tabeli wymieniono identyfikatory LCID języków obsługiwanych przez program Visual Studio.

|Język|Identyfikator LCID|
|--------------|----------|
|Chiński uproszczony|2052|
|Chiński (tradycyjny)|1028|
|Czeski|1029|
|Polski|1045|
|Francuski|1036|
|Niemiecki|1031|
|Włoski|1040|
|Japoński|1041|
|Koreański|1042|
|Polski|1045|
|portugalski (Brazylia)|1046|
|Rosyjski|1049|
|Hiszpański|3082|
|Turecki|1055

## <a name="example"></a>Przykład

W tym przykładzie ładuje IDE z ciągami zasobów w języku angielskim.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Ustawienia międzynarodowe, Środowisko, Opcje — okno dialogowe](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)
