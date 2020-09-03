---
title: Polecenie czujki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e585064bb50db7a0497c6b96e428a662e953ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604834"
---
# <a name="watch-command"></a>Czujka — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tworzy i otwiera określone wystąpienie okna **czujka** . Można użyć okna **czujki** do obliczenia wartości zmiennych, wyrażeń i rejestrów, aby edytować te wartości i zapisać wyniki.

## <a name="syntax"></a>Składnia

```
Debug.Watch[index]
```

## <a name="arguments"></a>Argumenty
 `index` Wymagane. Numer wystąpienia okna Czujka.

## <a name="remarks"></a>Uwagi
 Wartość `index` musi być liczbą całkowitą. Prawidłowe wartości to 1, 2, 3 lub 4.

## <a name="example"></a>Przykład

```
>Debug.Watch1
```

## <a name="see-also"></a>Zobacz też
 Zmienne [i ustawienia regionalne systemu Windows](../../debugger/autos-and-locals-windows.md) [instrukcje: Edytowanie wartości w oknie zmiennych](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5) [instrukcje: korzystanie z okna dialogowego QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [poleceń programu Visual Studio](../../ide/reference/visual-studio-commands.md) okno [polecenia](../../ide/reference/command-window.md) [Znajdź/polecenia](../../ide/find-command-box.md) w [programie Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
