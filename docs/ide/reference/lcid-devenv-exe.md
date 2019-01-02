---
title: -LCID (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5c3f8633721a4568b81fab31d8fe91a4c33be2f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852076"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Ustawia domyślny język używany dla tekstu, waluty i innych wartości w ramach zintegrowanego środowiska programistycznego (IDE).

## <a name="syntax"></a>Składnia

```cmd
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Argumenty
 `LocaleID` Wymagane. Identyfikator LCID (identyfikator ustawień regionalnych) języka, które określisz.

## <a name="remarks"></a>Uwagi
 Ładuje środowisko IDE i ustawia domyślny język naturalny dla środowiska. Ta zmiana jest zachowywane między sesjami i przedstawiane na **ustawienia międzynarodowe** okienku **środowiska** opcji na liście **opcje** okno dialogowe w środowisku IDE.

 Jeśli określony język nie jest dostępne w systemie użytkownika, przełącznik/LCID jest ignorowany.

 Poniższa tabela zawiera identyfikatory LCID języków obsługiwanych przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

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

```cmd
devenv /LCID 1033
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Ustawienia międzynarodowe, Środowisko, Opcje — okno dialogowe](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)