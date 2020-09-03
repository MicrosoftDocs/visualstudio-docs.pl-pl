---
title: Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0157b1ade2c38a2c10920b9674d7c9a58ac036b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156529"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie zdalne używa modelu DCOM do komunikacji między komputerami lokalnymi i zdalnymi w następujących sytuacjach:  
  
- Debuger jest ustawiony na **natywny tryb zgodności** lub **zarządzany tryb zgodności** jest sprawdzany na stronie **Narzędzia/Opcje/debugowanie**  
  
- Debugujesz zarządzany kod C++ (C++/CLI).  
  
- W Visual Studio 2013, po **włączeniu opcji Edytuj natywny i Kontynuuj** jest zaznaczone na stronie **Narzędzia/Opcje/debugowanie**  
  
- Niektóre scenariusze debugowania innych firm  
  
  Ten błąd występuje, gdy proces programu Visual Studio nie może uwierzytelnić się samodzielnie (lub podane poświadczenia zostały uznane za niewystarczające) do procesu zdalnego debugera za pośrednictwem modelu DCOM. Co najmniej jedno z następujących obejść może rozwiązać ten problem:  
  
- Wyłącz  **tryb zgodności natywnej** i **tryb zgodności zarządzanej**.  
  
- W Visual Studio 2013 Wyłącz opcję **Włącz natywną edycję i Kontynuuj**.  
  
- Uruchom ponownie oba komputery.  
  
- Jeśli debugowanie zdalne wymaga wprowadzenia poświadczeń, zaznacz opcję zapisania poświadczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)
