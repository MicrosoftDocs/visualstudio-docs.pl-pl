---
title: 'Błąd: Zapora nie ma uwierzytelniania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db13165c584399952dc491cf714ac84ee4de7598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697428"
---
# <a name="error-firewall-no-authentication"></a>Błąd: Brak uwierzytelnienia zapory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapora połączenia internetowego na komputerze zdalnym nie została skonfigurowana w taki sposób, aby zezwalała na debugowanie zdalne. W przypadku zdalnego debugowania z `No Authentication` , msvsmon.exe należy dodać do listy wyjątków. Może być również konieczne otworzenie niektórych portów IPSEC.  
  
> [!NOTE]
> Zdalny debuger jest w stanie automatycznie konfigurować zaporę systemu Windows. W przypadku korzystania z zapory innej niż Zapora systemu Windows, takiej jak Zapora oprogramowania innej firmy lub zapora sprzętowa, należy ręcznie skonfigurować zaporę, aby umożliwić zdalne debugowanie. W tym celu Zezwól na ruch na portach TCP/IP, które msvsmon.exe nasłuchuje. Domyślnie są to porty 4018 i 4019, gdzie 4018 jest używany we wszystkich systemach operacyjnych, a 4019 jest używany tylko w systemie Windows x64 do zezwalania na Debugowanie procesów x86.  
  
 Aby uzyskać więcej informacji, zobacz [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).
