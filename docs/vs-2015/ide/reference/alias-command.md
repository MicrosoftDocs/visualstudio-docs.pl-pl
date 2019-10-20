---
title: Alias — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6da744b0db9e41cd1e5039a1bd0d5c93bc4c734a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651688"
---
# <a name="alias-command"></a>Alias — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tworzy nowy alias dla kompletnego polecenia, kompletne polecenie i argumenty lub inny alias.

> [!TIP]
> Wpisanie `>alias` bez żadnych argumentów wyświetla bieżącą listę aliasów i ich definicje.

## <a name="syntax"></a>Składnia

```
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumenty
 `aliasname` opcjonalny. Nazwa nowego aliasu. Jeśli nie podano żadnej wartości dla `aliasname`, zostanie wyświetlona lista bieżących aliasów i ich definicji.

 `aliasstring` opcjonalny. Pełna nazwa polecenia lub istniejący alias oraz wszystkie parametry, które chcesz utworzyć jako alias. Jeśli nie podano wartości dla `aliasstring`, zostanie wyświetlona nazwa aliasu i ciąg aliasu dla określonego aliasu.

## <a name="switches"></a>Przełączniki
 /DELETE lub/del lub/d opcjonalne. Usuwa określony alias, usuwając go z autouzupełniania.

 /Reset opcjonalne. Resetuje listę wstępnie zdefiniowanych aliasów do jej oryginalnych ustawień. Oznacza to, że przywraca wszystkie wstępnie zdefiniowane aliasy i usuwa wszystkie aliasy zdefiniowane przez użytkownika.

## <a name="remarks"></a>Uwagi
 Ponieważ aliasy reprezentują polecenia, muszą one znajdować się na początku wiersza polecenia.

 Po wydaniu tego polecenia, należy uwzględnić przełączniki natychmiast po poleceniu, nie po aliasach, w przeciwnym razie sam przełącznik zostanie dołączony jako część ciągu aliasu.

 Przełącznik `/reset` prosi o potwierdzenie przed przywróceniem aliasów. Nie ma żadnej krótkiej formy `/reset`.

## <a name="examples"></a>Przykłady
 W tym przykładzie tworzony jest nowy alias, `upper` w celu wykonania polecenia Edit. MakeUpperCase.

```
>Tools.Alias upper Edit.MakeUpperCase
```

 Ten przykład usuwa alias, `upper`.

```
>Tools.alias /delete upper
```

 Ten przykład wyświetla listę wszystkich bieżących aliasów i definicji.

```
>Tools.Alias
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
