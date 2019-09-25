---
title: Debugowanie klientów i serwerów za pomocą debugowania RPC COM | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2cca09e917cddffd0d1d844db14ae8a4ca4f0088
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211074"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Porady: Debugowanie klientów i serwerów COM za pomocą debugowania RPC
Debugowanie zdalnego wywołania (procedur RPC) procedury można użyć do debugowania aplikacji typu klient/serwer COM. Konieczne jest włączenie debugowania z niej korzystać RPC. Z włączonym debugowaniem RPC, po kroku do wywołania serwera z klienta, debuger dołącza do serwera i umożliwia debugowanie kodu. Gdy debuger jest dołączony, mogą używać wszystkich funkcji debugera, procesy klienta i serwera.

### <a name="to-enable-rpc-debugging"></a>Aby włączyć debugowanie RPC

1. Na **narzędzia** menu, kliknij przycisk **opcje**.

2. W **opcje** okno dialogowe, kliknij przycisk **debugowanie** folderu.

3. Kliknij przycisk **natywnych** strony.

4. Wybierz **debugowania RPC** pole wyboru.

    > [!NOTE]
    > Aby debugować wywołania RPC, musi mieć uprawnienia administratora lub użytkownik zaawansowany.

    > [!NOTE]
    > Przechodzenie do serwera zdalnego z systemem Microsoft Windows Vista RPC będzie działać tylko wtedy, gdy debuger natywny jest dołączony do serwera zdalnego. W przeciwnym razie wywołania RPC zakończy się niepowodzeniem bez komunikatu o błędzie. W przeciwnym razie wywołania RPC zostanie ukończone, ale wkroczenia do wywołania RPC nie będzie działać.

## <a name="see-also"></a>Zobacz też
- [Debugowanie kontenera i serwera COM](../debugger/com-server-and-container-debugging.md)
- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)