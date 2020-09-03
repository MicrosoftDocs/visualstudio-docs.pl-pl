---
title: Dodawanie atrybutu DebuggerDisplay
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 611df048d4ce569c10ae933be9053acf1174c06f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85290585"
---
# <a name="add-debuggerdisplay-attribute"></a>Dodawanie atrybutu DebuggerDisplay

Ta generacja kodu ma zastosowanie do:

- C#

**Co:** [Atrybut DebuggerDisplay](https://docs.microsoft.com/visualstudio/debugger/using-the-debuggerdisplay-attribute) kontroluje sposób wyświetlania obiektu, właściwości lub pola w oknach zmiennych debugera.

**Kiedy:** Chcesz [przypiąć właściwości](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor#pin-properties-in-datatips) w debugerze programowo w kodzie.

**Dlaczego:** Przypinanie właściwości pozwala na szybkie inspekcje obiektów według ich właściwości poprzez propagację tej właściwości na górę listy właściwości obiektu w debugerze. 

## <a name="how-to"></a>Porady

1. Umieść kursor na typie, delegatze, właściwości lub polu. 

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz pozycję **Dodaj atrybut DebuggerDisplay**.

    ![Generowanie operatorów porównania](media/add-debugger-display-attribute.png)

3. Atrybut DebuggerDisplay zostanie dodany wraz z metodą autodostrajania, która zwraca domyślny element ToString (). 

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
