---
title: -LCID (devenv.exe)
description: Dowiedz się, jak za pomocą przełącznika wiersza polecenia LCID devenv ustawić domyślny język używany dla tekstu, waluty i innych wartości w środowisku IDE.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: eda3a4d9242655af1b018664273ceb693c7e775c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96043988"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Ustawia domyślny język używany na potrzeby tekstu, waluty i innych wartości w IDE.

## <a name="syntax"></a>Składnia

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argumenty

- *LocaleID*

  Wymagane. Identyfikator ustawień regionalnych (LCID) określonego języka.

## <a name="remarks"></a>Uwagi

Ładuje IDE i ustawia domyślny język naturalny dla środowiska. Ta zmiana jest utrwalana między sesjami, a środowisko IDE pokazuje tę zmianę w polu **Narzędzia**  >  **Opcje**  >  **środowisko**  >  **ustawień międzynarodowych**  >  **Language** .

Jeśli określony język nie jest dostępny w systemie, `/LCID` przełącznik zostanie zignorowany.

W poniższej tabeli przedstawiono identyfikatory LCID języków obsługiwanych przez program Visual Studio.

|Język|Identyfikator LCID|
|--------------|----------|
|Chiński (uproszczony)|2052|
|Chiński (tradycyjny)|1028|
|Czeski|1029|
|Angielski|1045|
|Francuski|1036|
|Niemiecki|1031|
|Włoski|1040|
|japoński|1041|
|Koreański|1042|
|Polski|1045|
|Portugalski (Brazylia)|1046|
|Rosyjski|1049|
|Hiszpański|3082|
|Turecki|1055

## <a name="example"></a>Przykład

Ten przykład ładuje środowisko IDE z ciągami zasobów w języku angielskim.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Ustawienia międzynarodowe, Środowisko, Opcje — okno dialogowe](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)
