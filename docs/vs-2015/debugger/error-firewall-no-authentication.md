---
title: 'Błąd: Brak uwierzytelnienia zapory | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: eb963afb4a1cbc029ee8490a9c35d1b09e8c3338
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447324"
---
# <a name="error-firewall-no-authentication"></a>Błąd: Brak uwierzytelnienia zapory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nie skonfigurowano Zapora połączenia internetowego na komputerze zdalnym w celu zezwolenia na debugowanie zdalne. Zdalne debugowanie przy użyciu `No Authentication`, msvsmon.exe musi być dodany do listy wyjątków. Otwieranie Niektóre porty protokołu IPSEC może być konieczne także.  
  
> [!NOTE]
> Zdalny debuger jest w stanie automatycznie skonfigurować zaporę Windows. W przypadku używania innej zapory niż Zapora Windows, takiego jak Zapora sprzętu lub innej zapory programowej, zapory musi być ręcznie skonfigurowany do zezwolenia na debugowanie zdalne. W tym celu należy zezwolić na ruch na portach TCP/IP tego msvsmon.exe nasłuchuje. Domyślnie są to port 4018 i 4019, gdzie 4018 jest używany we wszystkich systemach operacyjnych i 4019 jest używana tylko na Windows x64 w celu zezwolenia na debugowanie x86 procesów.  
  
 Aby uzyskać więcej informacji, zobacz [Ustaw się narzędzi zdalnych na urządzeniu](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).
