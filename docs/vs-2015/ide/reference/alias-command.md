---
title: Alias — polecenie | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4260804760b4abe55f6a62efa4841ad08dead1b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753273"
---
# <a name="alias-command"></a>Alias — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Tworzy nowy alias dla kompletnego polecenia, kompletne polecenie i argumenty lub inny alias.  
  
> [!TIP]
>  Wpisywanie `>alias` bez żadnych argumentów Wyświetla bieżącą listę aliasów i ich definicje.  
  
## <a name="syntax"></a>Składnia  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## <a name="arguments"></a>Argumenty  
 `aliasname`  
 Opcjonalna. Nazwa nowego pola alias. Jeśli nie dostarczono żadnej wartości dla `aliasname`, zostanie wyświetlona lista bieżących aliasów i ich definicje.  
  
 `aliasstring`  
 Opcjonalna. Pełna nazwa polecenia lub istniejący alias i wszystkie parametry, które chcesz utworzyć jako alias. Jeśli nie dostarczono żadnej wartości dla `aliasstring`, nazwa aliasu i ciągi aliasów dla określonych aliasów Wyświetla.  
  
## <a name="switches"></a>Przełączniki  
 / DELETE lub/DEL lub /d  
 Opcjonalna. Usuwa określony alias, usuwając go z automatycznego uzupełniania.  
  
 /reset  
 Opcjonalna. Resetuje listę wstępnie zdefiniowanych aliasów pierwotne ustawienia. Oznacza to, że przywraca wszystkie wstępnie zdefiniowane aliasy i usuwa wszystkie aliasy zdefiniowane przez użytkownika.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ aliasy stanowią polecenia, muszą być umieszczone na początku wiersza polecenia.  
  
 Po wykonaniu tego polecenia, należy uwzględnić przełączniki natychmiast po poleceniu nie po aliasach, w przeciwnym razie sam przełącznik zostanie dołączony jako część ciąg aliasu.  
  
 `/reset` Przełącznik prosi o potwierdzenie zanim aliasy zostaną przywrócone. Brak żadnych krótkich form `/reset`.  
  
## <a name="examples"></a>Przykłady  
 Ten przykład tworzy nowy alias `upper`, dla pełnego polecenia Edit.MakeUpperCase.  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 W tym przykładzie Usuwa alias, `upper`.  
  
```  
>Tools.alias /delete upper  
```  
  
 W tym przykładzie wyświetla listę wszystkich bieżących aliasów i definicji.  
  
```  
>Tools.Alias  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
