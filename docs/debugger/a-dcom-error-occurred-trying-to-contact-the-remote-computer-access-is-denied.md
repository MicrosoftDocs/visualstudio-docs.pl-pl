---
title: Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu. | Microsoft Docs
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
ms.openlocfilehash: 93dfb374e693c6483ff80737b8715e4abc570bf0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009706"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu.
Zdalne debugowanie używa modelu DCOM do komunikacji między komputerami lokalnymi i zdalnymi w następujących sytuacjach:  
  
- Debuger jest ustawiona na **macierzysty tryb zgodności** lub **trybu zgodności zarządzanej** jest zaewidencjonowany **Narzędzia > Opcje > debugowanie** strony  
  
- Debugowany zarządzany kod C++ (C + +/ CLI) kod.  
  
- W programie Visual Studio 2013 podczas **Włączanie natywnego Edytuj i Kontynuuj** jest zaewidencjonowany **Narzędzia > Opcje > debugowanie** strony  
  
- Niektóre innych firm debugowania scenariuszy  
  
  Ten błąd występuje, gdy proces programu Visual Studio nie może uwierzytelniać (lub podane poświadczenia zostały uznane za niewystarczające) do procesu zdalnego debugera za pośrednictwem protokołów DCOM. Co najmniej jedno z następujących rozwiązań może rozwiązać ten problem:  
  
- Wyłącz **natywny tryb zgodności** i **trybu zgodności zarządzanej**.  
  
- W programie Visual Studio 2013, wyłącz **Włączanie natywnego Edytuj i Kontynuuj**.  
  
- Ponowne uruchomienie obu komputerów.  
  
- Jeśli zdalne debugowanie wymaga wprowadzania poświadczeń, zaznacz opcję zapisania poświadczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)