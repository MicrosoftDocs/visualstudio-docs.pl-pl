---
title: Widok procesów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ba60021410f1965e05f7c5479231013d53cb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62904235"
---
# <a name="processes-view"></a>Widok procesów
Widok procesy Wyświetla drzewo wszystkich aktywnych procesów w systemie. Zostanie wyświetlony identyfikator procesu i nazwa modułu. Użyj widoku procesy, jeśli chcesz sprawdzić konkretny proces systemowy, który zwykle odpowiada programowi wykonującemu. Procesy są identyfikowane przez nazwy modułów lub wyznaczono "procesy systemowe".

 System Microsoft Windows obsługuje wiele procesów. Każdy proces może mieć jeden lub więcej wątków, a każdy wątek może mieć jedno lub więcej skojarzonych okien najwyższego poziomu. Każde okno najwyższego poziomu może być własnością serii systemu Windows. Symbol + wskazuje, że poziom jest zwinięty. Zwinięty widok składa się z jednej linii na proces. Kliknij symbol +, aby rozwinąć poziom.

 Użyj widoku procesy, jeśli chcesz sprawdzić konkretny proces systemowy, który zwykle odpowiada programowi wykonującemu. Procesy są identyfikowane przez nazwy modułów lub wyznaczono "procesy systemowe". Aby znaleźć proces, Zwiń drzewo i przeszukaj listę.

## <a name="procedures"></a>Procedury

#### <a name="to-open-the-processes-view"></a>Aby otworzyć widok procesy

1. Z menu **Spy** wybierz pozycję **procesy**.

   ![Widok procesów&#43;&#43; Spy](../debugger/media/spy--_processes.png "_Processes Spy + +") Widok procesów w programie Spy + +

   Powyższy rysunek przedstawia widok procesy z rozwiniętymi węzłami proces i wątek.

### <a name="in-this-section"></a>W tej sekcji
 [Wyszukiwanie procesu w widoku procesów](../debugger/how-to-search-for-a-process-in-processes-view.md) Wyjaśnia, jak znaleźć konkretny proces w widoku procesy.

 [Wyświetlanie właściwości procesu](../debugger/how-to-display-process-properties.md) Wyjaśnia, jak wyświetlić więcej informacji o komunikacie.

### <a name="related-sections"></a>Sekcje pokrewne
 [Widoki Spy + +](../debugger/spy-increment-views.md) Wyjaśnia widoki drzewa Spy + + systemu Windows, komunikatów, procesów i wątków.

 [Korzystanie z programu Spy + +](../debugger/using-spy-increment.md) Wprowadzenie do narzędzia Spy + + i wyjaśnienie, jak można go użyć.

 [Wyszukiwanie procesów](../debugger/process-search-dialog-box.md) — okno dialogowe Służy do znajdowania węzła dla określonego procesu w widoku procesy.

 Okno [dialogowe właściwości procesu](../debugger/process-properties-dialog-box.md) Wyświetla właściwości procesu wybranego w widoku procesy.

 [Spy + + — Odwołanie](../debugger/spy-increment-reference.md) Zawiera sekcje opisujące poszczególne menu Spy + + i okna dialogowego.