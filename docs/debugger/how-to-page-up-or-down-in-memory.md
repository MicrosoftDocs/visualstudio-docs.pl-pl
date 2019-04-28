---
title: 'Instrukcje: Page Up lub w dół w pamięci | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b8452100eb744d019c0f4c8d5e62566ac761210
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894024"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Instrukcje: Page Up lub w dół w pamięci

Podczas wyświetlania zawartości pamięci w **pamięci** okna lub **dezasemblacji** okna, można użyć pionowy pasek przewijania można przenieść w górę lub w dół w obszarze pamięci.

### <a name="to-page-up-or-down-in-memory"></a>Stronę w górę lub w dół w pamięci

1. Aby stronę w dół (przeniesienie na wyższe adresu pamięci), kliknij pasek przewijania pionowego poniżej suwaka.

2. Stronę w górę (przeniesienie na niższym adresu pamięci), kliknij pasek przewijania pionowego powyżej przycisku suwaka.

   Można również zauważyć, że pionowy pasek przewijania działa w sposób niestandardowy. Przestrzeni adresowej nowoczesnych komputera jest bardzo duży i będzie można łatwo giną Przechwytywanie przycisku przewijania suwaka, a następnie przeciągając go do losowo wybranej lokalizacji. Z tego powodu uchwytu jest "springloaded" i zawsze pozostaje w środkowej części paska przewijania. W aplikacjach kodu macierzystego można stronę w górę lub w dół, ale nie można swobodnie Przewiń o.

   W zarządzanych aplikacjach dezasemblacji jest ograniczona do jednej funkcji, a następnie można przewijać w zwykły sposób.

   Zauważysz, że wyższe adresy są wyświetlane w dolnej części okna. Aby wyświetlić adres wyższe, należy przenieść w dół, nie rozmiarze.

#### <a name="to-move-up-or-down-one-instruction"></a>Aby przenieść w górę lub dół jednej instrukcji

- Kliknij strzałkę w górę lub w dół pionowy pasek przewijania.

## <a name="see-also"></a>Zobacz też
- [Okna pamięci](../debugger/memory-windows.md)
- [Instrukcje: Korzystanie z okna dezasemblacji](../debugger/how-to-use-the-disassembly-window.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)