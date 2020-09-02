---
title: 'Instrukcje: debugowanie klientów i serwerów COM za pomocą debugowania RPC | Microsoft Docs'
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
ms.openlocfilehash: fda2a10cd559f940ab87e5cc8c26f5b47dbec194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837309"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Porady: debugowanie klientów i serwerów COM za pomocą debugowania RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowania zdalnego wywołania procedury (RPC) można używać do debugowania aplikacji klient/serwer COM. Musisz włączyć debugowanie RPC, aby go używać. Po włączeniu debugowania RPC po przekroczeniu wywołania serwera z klienta debuger dołącza do serwera i umożliwia debugowanie jego kodu. Po dołączeniu debugera można użyć wszystkich funkcji debugera zarówno w przypadku procesów klienta, jak i serwera.  
  
### <a name="to-enable-rpc-debugging"></a>Aby włączyć debugowanie RPC  
  
1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).  
  
2. W oknie dialogowym **Opcje** kliknij folder **debugowanie** .  
  
3. Kliknij stronę **natywną** .  
  
4. Zaznacz pole wyboru **debugowanie wywołania RPC** .  
  
    > [!NOTE]
    > Aby debugować wywołania RPC, musisz mieć uprawnienia administratora lub użytkownika zaawansowanego.  
  
    > [!NOTE]
    > Wywołanie RPC do zdalnego serwera z systemem Microsoft Windows Vista będzie działać tylko wtedy, gdy do zdalnego serwera jest dołączony debuger natywny. W przeciwnym razie wywołanie RPC zakończy się niepowodzeniem bez komunikatu o błędzie. W przeciwnym razie wywołanie RPC zostanie ukończone, ale wywołanie wywołania RPC nie będzie działało.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kontenera i serwera COM](../debugger/com-server-and-container-debugging.md)   
 [Debugowanie w Visual Studio](../debugger/debugging-in-visual-studio.md)
