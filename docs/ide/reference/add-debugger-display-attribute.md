---
title: Dodawanie atrybutu DebuggerDisplay
description: Dowiedz się, jak dodać atrybut DebuggerDisplay, aby kontrolować sposób wyświetlania przez okno zmiennych debugera obiektu, właściwości lub pola.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2166f7876909f62d9d16a2a6d5ec126d4544193e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956727"
---
# <a name="add-debuggerdisplay-attribute"></a>Dodawanie atrybutu DebuggerDisplay

Ta generacja kodu ma zastosowanie do:

- C#

**Co:** [Atrybut DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) kontroluje sposób wyświetlania obiektu, właściwości lub pola w oknach zmiennych debugera.

**Kiedy:** Chcesz [przypiąć właściwości](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) w debugerze programowo w kodzie.

**Dlaczego:** Przypinanie właściwości pozwala na szybkie inspekcje obiektów według ich właściwości poprzez propagację tej właściwości na górę listy właściwości obiektu w debugerze. 

## <a name="how-to"></a>Porady

1. Umieść kursor na typie, delegatze, właściwości lub polu. 

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz pozycję **Dodaj atrybut DebuggerDisplay**.

    ![Generowanie operatorów porównania](media/add-debugger-display-attribute.png)

3. Atrybut DebuggerDisplay zostanie dodany wraz z metodą autodostrajania, która zwraca domyślny element ToString (). 

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)