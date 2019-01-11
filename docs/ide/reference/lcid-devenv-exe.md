---
title: -LCID (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42da279a64f04bca7775440f803e7a26e6bd2dc8
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227307"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Ustawia domyślny język używany dla tekstu, waluty i innych wartości w środowisku IDE.

## <a name="syntax"></a>Składnia

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argumenty

- *Identyfikator ustawień regionalnych*

  Wymagana. Identyfikator ustawień regionalnych (LCID) języka, które określisz.

## <a name="remarks"></a>Uwagi

Ładuje środowisko IDE i ustawia domyślny język naturalny dla środowiska. Ta zmiana jest zachowywane między sesjami i IDE Wyświetla ta zmiana w **narzędzia** > **opcje** > **środowiska**  >  **Ustawienia międzynarodowe** > **języka** pole.

Jeśli określony język nie jest dostępna w systemie, `/LCID` jest ignorowana.

W poniższej tabeli wymieniono LCID języki obsługiwane przez program Visual Studio.

|Język|LCID|
|--------------|----------|
|Chiński uproszczony|2052|
|Chiński (tradycyjny)|1028|
|Angielski|1033|
|Francuski|1036|
|niemiecki|1031|
|Włoski|1040|
|japoński|1041|
|koreański|1042|
|Hiszpański|3082|

## <a name="example"></a>Przykład

W tym przykładzie ładuje środowisko IDE z ciągów zasobów w języku angielskim.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Ustawienia międzynarodowe, Środowisko, Opcje — okno dialogowe](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)