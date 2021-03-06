---
title: Kod mieszany & brakujące informacje w oknie stosu wywołań
description: W przypadku programów w trybie mieszanym (natywny i zarządzany) debuger nie zawsze może wyświetlić kompletnego stosu wywołań. Poznaj możliwe rozbieżności, gdy kod natywny wywołuje kod zarządzany.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 793d60c9bc550b0f29ac48e50a95dab601750ad4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885108"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Kod mieszany i brakujące informacje w oknie stosu wywołań
Ze względu na różnice między stosami wywołań dla kodu zarządzanego i natywnego debuger nie może zawsze pokazać kompletnego stosu wywołań, gdy typy kodu są mieszane. Gdy kod natywny wywołuje kod zarządzany, można zauważyć następujące rozbieżności w oknie **stosu wywołań** :

- W oknie **stosu wywołań** może brakować ramki natywnej bezpośrednio nad kodem zarządzanym. Aby uzyskać więcej informacji, zobacz [jak: Wyjdź z kodu zarządzanego, gdy w oknie stosu wywołań brakuje ramek natywnych](how-to-use-the-call-stack-window.md).

- W przypadku aplikacji w trybie mieszanym uruchomionych poza debugerem okno **stos wywołań** może wyświetlać tylko kod zarządzany i żadna z ramek natywnych nie będzie widoczna.

  Oba przypadki są dość rzadkie. W większości natywnych wywołań do kodu zarządzanego, stosy wywołań są wyświetlane poprawnie.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md)