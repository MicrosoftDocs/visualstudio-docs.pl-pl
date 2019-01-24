---
title: 'Instrukcje: Debugowanie klientów i serwerów za pomocą debugowania RPC COM | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1235abfc6e8a2c384b02fd1d48a859063c058d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766614"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Instrukcje: Debugowanie klientów i serwerów za pomocą debugowania RPC COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie zdalnego wywołania (procedur RPC) procedury można użyć do debugowania aplikacji typu klient/serwer COM. Konieczne jest włączenie debugowania z niej korzystać RPC. Z włączonym debugowaniem RPC, po kroku do wywołania serwera z klienta, debuger dołącza do serwera i umożliwia debugowanie kodu. Gdy debuger jest dołączony, mogą używać wszystkich funkcji debugera, procesy klienta i serwera.  
  
### <a name="to-enable-rpc-debugging"></a>Aby włączyć debugowanie RPC  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  W **opcje** okno dialogowe, kliknij przycisk **debugowanie** folderu.  
  
3.  Kliknij przycisk **natywnych** strony.  
  
4.  Wybierz **debugowania RPC** pole wyboru.  
  
    > [!NOTE]
    >  Aby debugować wywołania RPC, musi mieć uprawnienia administratora lub użytkownik zaawansowany.  
  
    > [!NOTE]
    >  Przechodzenie do serwera zdalnego z systemem Microsoft Windows Vista RPC będzie działać tylko wtedy, gdy debuger natywny jest dołączony do serwera zdalnego. W przeciwnym razie wywołania RPC zakończy się niepowodzeniem bez komunikatu o błędzie. W przeciwnym razie wywołania RPC zostanie ukończone, ale wkroczenia do wywołania RPC nie będzie działać.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kontenera i serwera COM](../debugger/com-server-and-container-debugging.md)   
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)
