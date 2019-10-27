---
title: Debugowanie klientów i serwerów COM za pomocą debugowania RPC | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83fdfa65f4efb6f0bc0b99eac27ae0e57c79e3cd
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733691"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Porady: debugowanie klientów i serwerów COM za pomocą debugowania RPC
Debugowania zdalnego wywołania procedury (RPC) można używać do debugowania aplikacji klient/serwer COM. Musisz włączyć debugowanie RPC, aby go używać. Po włączeniu debugowania RPC po przekroczeniu wywołania serwera z klienta debuger dołącza do serwera i umożliwia debugowanie jego kodu. Po dołączeniu debugera można użyć wszystkich funkcji debugera zarówno w przypadku procesów klienta, jak i serwera.

### <a name="to-enable-rpc-debugging"></a>Aby włączyć debugowanie RPC

1. W menu **Narzędzia** kliknij pozycję **Opcje**.

2. W oknie dialogowym **Opcje** kliknij folder **debugowanie** .

3. Kliknij stronę **natywną** .

4. Zaznacz pole wyboru **debugowanie wywołania RPC** .

    > [!NOTE]
    > Aby debugować wywołania RPC, musisz mieć uprawnienia administratora lub użytkownika zaawansowanego.

    > [!NOTE]
    > Wywołanie RPC do zdalnego serwera z systemem Microsoft Windows Vista będzie działać tylko wtedy, gdy do zdalnego serwera jest dołączony debuger natywny. W przeciwnym razie wywołanie RPC zakończy się niepowodzeniem bez komunikatu o błędzie. W przeciwnym razie wywołanie RPC zostanie ukończone, ale wywołanie wywołania RPC nie będzie działało.

## <a name="see-also"></a>Zobacz także
- [Debugowanie kontenera i serwera COM](../debugger/com-server-and-container-debugging.md)
- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)