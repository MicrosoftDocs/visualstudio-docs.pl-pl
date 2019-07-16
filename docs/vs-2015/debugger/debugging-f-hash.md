---
title: Debugowanie F# | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51a8e43268718421a90d051f0d4d9b6afa96980e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156688"
---
# <a name="debugging-f"></a>Debugowanie F\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie F# jest podobne do debugowania jakiegokolwiek języka zarządzanego, z pewnymi wyjątkami:

- **Autos** nie są wyświetlane w oknie F# zmiennych.

- Edytuj i Kontynuuj nie jest obsługiwana dla F#. Edytowanie F# kodu podczas sesji debugowania jest możliwe, ale należy unikać. Ponieważ zmiany w kodzie nie są stosowane podczas sesji debugowania, edytowanie F# kodu podczas debugowania spowoduje niezgodność między kodem źródłowym i debugowany kod.

- Debuger nie może rozpoznać F# wyrażenia. Wprowadzenia wyrażenia, w oknie debugera lub okno dialogowe podczas F# profilowanie, musi przetłumaczyć wyrażenia w C# składni. Podczas translacji F# wyrażenie C#, upewnij się, że należy pamiętać, że C# używa == jako operator porównania dla równości, które F# używa pojedynczego =.

## <a name="see-also"></a>Zobacz też

- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
