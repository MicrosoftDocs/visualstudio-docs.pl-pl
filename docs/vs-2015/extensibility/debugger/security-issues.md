---
title: Problemy z zabezpieczeniami | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704421"
---
# <a name="security-issues"></a>Problemy dotyczące zabezpieczeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby debugować programu przy użyciu programu Visual Studio, tylko wymagane uprawnienia są same deweloper musi zostać uruchomiony program. W tym zdalnego debugowania w większości sytuacji (czasami obejmujące innych usług, takich jak Internet Information Services mogą wymagać wyższego poziomu uprawnień).  
  
 Po uruchomieniu programu Visual Studio Menedżer debugowania procesów (menedżerów PDM) śledzi debugowanie procesów na komputerze lokalnym. Zdalnie program o nazwie msvsmon.exe został uruchomiony przez dewelopera obsługę zdalnego debugowania i udostępnić menedżerów PDM. (Zwróć uwagę, że msvsmon.exe nie jest usługą i musi zostać uruchomione ręcznie włączyć zdalne debugowanie na tym komputerze). Gdy program Visual Studio (lub msvsmon.exe) nie jest uruchomiona, żadne procesy nie są śledzone dla debugowania.  
  
 Oznacza to, że deweloper można debugować programy, które użytkownik wprowadzenie żadne specjalne uprawnienia. Deweloper może nawet debugować procesy uruchomione przez innego użytkownika, jeśli inne osoba jest członkiem tej samej grupy zabezpieczeń. I włączyć zdalne debugowanie, konieczne jest tylko do skopiowania niezbędne pliki do zdalnego komputera i uruchomić msvsmon.exe (zobacz [Ustaw się narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) Aby uzyskać więcej informacji).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)   
 [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md)   
 [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
