---
title: 'Instrukcje: Edytowanie wartości rejestru | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3ccaa124b64ad462f633e760695f931afaae531
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733416"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Instrukcje: Edytowanie wartości rejestru (C#, C++, Visual Basic,) F#

Okno rejestry jest dostępne tylko wtedy, gdy w oknie dialogowym **Opcje** jest **włączone debugowanie na** poziomie adresu.

### <a name="to-change-the-value-of-a-register"></a>Aby zmienić wartość rejestru

1. W oknie **rejestry** Użyj klawisza TAB lub myszy, aby przenieść punkt wstawiania do wartości, którą chcesz zmienić. Po rozpoczęciu wpisywania kursor musi znajdować się przed wartością, która ma zostać zastąpiona.

2. Wpisz nową wartość.

    > [!CAUTION]
    > Zmiana wartości rejestru (szczególnie w rejestrach EIP i EBP) może mieć wpływ na wykonywanie programu.

    > [!CAUTION]
    > Edytowanie wartości zmiennoprzecinkowych może spowodować powstanie nieścisłych niedokładności z powodu konwersji dziesiętnej na binarną składników ułamkowych. Nawet pozornie niewielkiej ilości Edycja może spowodować zmianę niektórych najmniej znaczących bitów w rejestrze zmiennoprzecinkowym.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)