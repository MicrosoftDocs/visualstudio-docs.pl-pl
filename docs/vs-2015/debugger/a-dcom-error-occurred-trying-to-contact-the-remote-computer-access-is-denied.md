---
title: Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu. | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ec23d23934268ebb50699bc1de3d17b75d357d3a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770284"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Wystąpił błąd modelu DCOM podczas próby skontaktowania się z komputerem zdalnym. Odmowa dostępu.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zdalne debugowanie używa modelu DCOM do komunikacji między komputerami lokalnymi i zdalnymi w następujących sytuacjach:  
  
- Debuger jest ustawiona na **macierzysty tryb zgodności** lub **trybu zgodności zarządzanej** jest zaewidencjonowany **narzędzia / Opcje / Debugowanie** strony  
  
- Debugowany zarządzany kod C++ (C + +/ CLI) kod.  
  
- W programie Visual Studio 2013 gdy **Włączanie natywnego Edytuj i Kontynuuj** jest zaewidencjonowany **narzędzia / Opcje / Debugowanie** strony  
  
- Niektóre innych firm debugowania scenariuszy  
  
  Ten błąd występuje, gdy proces programu Visual Studio nie może uwierzytelniać (lub podane poświadczenia zostały uznane za niewystarczające) do procesu zdalnego debugera za pośrednictwem protokołów DCOM. Co najmniej jedno z następujących rozwiązań może rozwiązać ten problem:  
  
- Wyłącz **natywny tryb zgodności** i **trybu zgodności zarządzanej**.  
  
- W programie Visual Studio 2013, wyłącz **Włączanie natywnego Edytuj i Kontynuuj**.  
  
- Ponowne uruchomienie obu komputerów.  
  
- Jeśli zdalne debugowanie wymaga wprowadzania poświadczeń, zaznacz opcję zapisania poświadczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)



