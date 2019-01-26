---
title: 'Błąd: Brak uwierzytelnienia zapory | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e565d1372131272f8653df328dbbe9749a8b1ddb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035305"
---
# <a name="error-firewall-no-authentication"></a>Błąd: Brak uwierzytelnienia zapory
Nie skonfigurowano Zapora połączenia internetowego na komputerze zdalnym w celu zezwolenia na debugowanie zdalne. Zdalne debugowanie przy użyciu `No Authentication`, msvsmon.exe musi być dodany do listy wyjątków. Otwieranie Niektóre porty protokołu IPSEC może być konieczne także.  
  
> [!NOTE]
>  Zdalny debuger jest w stanie automatycznie skonfigurować zaporę Windows. W przypadku używania innej zapory niż Zapora Windows, takiego jak Zapora sprzętu lub innej zapory programowej, zapory musi być ręcznie skonfigurowany do zezwolenia na debugowanie zdalne. W tym celu należy zezwolić na ruch na portach TCP/IP tego msvsmon.exe nasłuchuje. Domyślnie są to port 4018 i 4019, gdzie 4018 jest używany we wszystkich systemach operacyjnych i 4019 jest używana tylko na Windows x64 w celu zezwolenia na debugowanie x86 procesów.  
  
 Aby uzyskać więcej informacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).