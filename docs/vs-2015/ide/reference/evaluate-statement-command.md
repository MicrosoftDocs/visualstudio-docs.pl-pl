---
title: Polecenie oszacowania instrukcji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657706"
---
# <a name="evaluate-statement-command"></a>Evaluate Statement — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Oblicza i wyświetla daną instrukcję.

## <a name="syntax"></a>Składnia

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argumenty
 Wymagane `text`. Instrukcja, która ma zostać obliczona.

## <a name="remarks"></a>Uwagi
 Okno używane do wprowadzania polecenia **EvaluateStatement** określa, czy znak równości (=) jest interpretowany jako operator porównania, czy jako operator przypisania.

 W oknie **polecenia** znak równości (=) jest interpretowany jako operator porównania. Tak więc, na przykład, jeśli wartości zmiennych `a` i `b` są różne, polecenie

```
>Debug.EvaluateStatement(a=b)
```

 zwróci wartość `false`.

 W oknie **bezpośrednim** , z przeciwieństwem, znak równości (=) jest interpretowany jako operator przypisania. Tak więc, na przykład, polecenie

```
>Debug.EvaluateStatement(a=b)
```

 zostanie przypisany do zmiennej `a` wartość `b` zmiennej.

## <a name="example"></a>Przykład

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Zobacz też
 [Polecenie Print polecenia](../../ide/reference/print-command.md) [poleceń programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno polecenia](../../ide/reference/command-window.md) [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
