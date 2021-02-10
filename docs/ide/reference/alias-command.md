---
title: Alias — Polecenie
description: Dowiedz się, jak za pomocą polecenia alias utworzyć nowy alias dla kompletnego polecenia, kompletne polecenie i argumenty lub inny alias.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a20a14cc0f48e86840b770aca934b188bf152dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969792"
---
# <a name="alias-command"></a>Alias — Polecenie
Tworzy nowy alias dla kompletnego polecenia, kompletne polecenie i argumenty lub inny alias.

> [!TIP]
> Wpisywanie `>alias` bez żadnych argumentów wyświetla bieżącą listę aliasów i ich definicje.

## <a name="syntax"></a>Składnia

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumenty
`aliasname`\
Opcjonalny. Nazwa nowego aliasu. Jeśli nie podano wartości dla `aliasname` , zostanie wyświetlona lista bieżących aliasów i ich definicji.

`aliasstring`\
Opcjonalny. Pełna nazwa polecenia lub istniejący alias oraz wszystkie parametry, które chcesz utworzyć jako alias. Jeśli nie podano wartości dla `aliasstring` , zostanie wyświetlona nazwa aliasu i ciąg aliasu dla określonego aliasu.

## <a name="switches"></a>Przełączniki
/DELETE lub/del lub/d\
Opcjonalny. Usuwa określony alias, usuwając go z autouzupełniania.

/Reset
Opcjonalny. Resetuje listę wstępnie zdefiniowanych aliasów do jej oryginalnych ustawień. Oznacza to, że przywraca wszystkie wstępnie zdefiniowane aliasy i usuwa wszystkie aliasy zdefiniowane przez użytkownika.

## <a name="remarks"></a>Uwagi
Ponieważ aliasy reprezentują polecenia, muszą one znajdować się na początku wiersza polecenia.

Po wydaniu tego polecenia, należy uwzględnić przełączniki natychmiast po poleceniu, nie po aliasach, w przeciwnym razie sam przełącznik zostanie dołączony jako część ciągu aliasu.

`/reset`Przełącznik monituje o potwierdzenie przed przywróceniem aliasów. Nie ma żadnej krótkiej formy `/reset` .

## <a name="examples"></a>Przykłady
W tym przykładzie tworzony jest nowy alias, `upper` dla pełnego polecenia Edit. MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Ten przykład usuwa alias, `upper` .

```cmd
>Tools.alias /delete upper
```

Ten przykład wyświetla listę wszystkich bieżących aliasów i definicji.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
