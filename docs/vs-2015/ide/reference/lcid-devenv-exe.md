---
title: -LCID (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: badb88abdf4b3ffd6140cb587b2b0add20630925
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672700"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ustawia domyślny język używany dla tekstu, waluty i innych wartości w zintegrowanym środowisku programistycznym (IDE).

## <a name="syntax"></a>Składnia

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Argumenty
 `LocaleID` Wymagane. Identyfikator LCID (identyfikatora ustawień regionalnych) określonego języka.

## <a name="remarks"></a>Uwagi
 Ładuje IDE i ustawia domyślny język naturalny dla środowiska. Ta zmiana jest utrwalana między sesjami i widoczna w okienku **Ustawienia międzynarodowe** opcji **środowisko** w oknie dialogowym **Opcje** w IDE.

 Jeśli określony język nie jest dostępny w systemie użytkownika, przełącznik/LCID jest ignorowany.

 W poniższej tabeli przedstawiono identyfikatory LCID języków obsługiwanych przez program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

|Język|Identyfikator LCID|
|--------------|----------|
|Chiński (uproszczony)|2052|
|Chiński (tradycyjny)|1028|
|Angielski|1045|
|Francuski|1036|
|Niemiecki|1031|
|Włoski|1040|
|japoński|1041|
|Koreański|1042|
|Hiszpański|3082|

## <a name="example"></a>Przykład
 Ten przykład ładuje środowisko IDE z ciągami zasobów w języku angielskim.

```
devenv /LCID 1033
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [Ustawienia międzynarodowe, środowisko, Opcje okno dialogowe](../../ide/reference/international-settings-environment-options-dialog-box.md) [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)
