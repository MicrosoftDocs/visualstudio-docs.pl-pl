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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 991886289ac2c2ee06e37476169dff6d2354a52e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659981"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Ustawia domyślny język używany na potrzeby tekstu, waluty i innych wartości w IDE.

## <a name="syntax"></a>Składnia

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argumenty

- *LocaleID*

  Wymagany. Identyfikator ustawień regionalnych (LCID) określonego języka.

## <a name="remarks"></a>Uwagi

Ładuje IDE i ustawia domyślny język naturalny dla środowiska. Ta zmiana jest utrwalana między sesjami, a środowisko IDE pokazuje tę zmianę w obszarze **narzędzia**  > **opcje**  > **środowisku**  > **Ustawienia międzynarodowe**  > **języka** .

Jeśli określony język nie jest dostępny w systemie, przełącznik `/LCID` jest ignorowany.

W poniższej tabeli przedstawiono identyfikatory LCID języków obsługiwanych przez program Visual Studio.

|Język|ISTNIEJĄCYCH|
|--------------|----------|
|Chiński uproszczony|2052|
|Chiński (tradycyjny)|1028|
|angielski|1033|
|francuski|1036|
|niemiecki|1031|
|Włoski|1040|
|japoński|1041|
|koreański|1042|
|Hiszpański|3082|

## <a name="example"></a>Przykład

Ten przykład ładuje środowisko IDE z ciągami zasobów w języku angielskim.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)
- [Ustawienia międzynarodowe, Środowisko, Opcje — okno dialogowe](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)