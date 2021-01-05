---
title: Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu.
titleSuffix: ''
description: "\"Wystąpił błąd DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu. Wyświetl informacje o tym odwołaniu zdalnego debugowania programu Visual Studio."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c430462a224cb4604c09984a5397e540ce752b8a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729200"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu.
Debugowanie zdalne używa modelu DCOM do komunikacji między komputerami lokalnymi i zdalnymi w następujących sytuacjach:

- Debuger jest ustawiony na **natywny tryb zgodności** lub **zarządzany tryb zgodności** jest sprawdzany na stronie **Narzędzia > opcje > debugowania**

- Debugujesz zarządzany kod C++ (C++/CLI).

- W Visual Studio 2013, po **włączeniu opcji Edytuj natywny i Kontynuuj** jest zaznaczone na stronie **narzędzia > opcje > debugowanie**

- Niektóre scenariusze debugowania innych firm

  Ten błąd występuje, gdy proces programu Visual Studio nie może uwierzytelnić się samodzielnie (lub podane poświadczenia zostały uznane za niewystarczające) do procesu zdalnego debugera za pośrednictwem modelu DCOM. Co najmniej jedno z następujących obejść może rozwiązać ten problem:

- Wyłącz  **tryb zgodności natywnej** i **tryb zgodności zarządzanej**.

- W Visual Studio 2013 Wyłącz opcję **Włącz natywną edycję i Kontynuuj**.

- Uruchom ponownie oba komputery.

- Jeśli debugowanie zdalne wymaga wprowadzenia poświadczeń, zaznacz opcję zapisania poświadczeń.

## <a name="see-also"></a>Zobacz też

- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)