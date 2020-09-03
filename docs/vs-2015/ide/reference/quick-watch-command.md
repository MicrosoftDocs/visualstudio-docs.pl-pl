---
title: Szybkie czujka — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da9ba9572e121a9eba74cd8d624789032f1bb4a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665668"
---
# <a name="quick-watch-command"></a>Szybka czujka — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyświetla wybrany lub określony tekst w polu wyrażenie okna [dialogowego QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). Za pomocą tego okna dialogowego można obliczyć bieżącą wartość zmiennej lub wyrażenia rozpoznawanego przez debuger lub zawartość rejestru. Ponadto można zmienić wartość dowolnej zmiennej innej niż stała lub zawartości dowolnego rejestru.

## <a name="syntax"></a>Składnia

```
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumenty
 `text` Obowiązkowe. Tekst, który ma zostać dodany do okna dialogowego **QuickWatch** .

## <a name="remarks"></a>Uwagi
 Jeśli `text` zostanie pominięty, aktualnie zaznaczony tekst lub słowo w kursorze zostanie dodane do okno wyrażeń kontrolnych.

## <a name="example"></a>Przykład

```
>Debug.QuickWatch
```

## <a name="see-also"></a>Zobacz też
 [Instrukcje: korzystanie z okna dialogowego QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [poleceń programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno polecenia](../../ide/reference/command-window.md) [Znajdź/polecenia](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
