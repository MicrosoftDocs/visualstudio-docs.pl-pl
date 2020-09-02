---
title: Problemy z zabezpieczeniami | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704421"
---
# <a name="security-issues"></a>Problemy z zabezpieczeniami
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aby debugować program przy użyciu programu Visual Studio, wymagane są te same uprawnienia, które deweloper potrzebuje do uruchomienia programu. Obejmuje to zdalne debugowanie w większości sytuacji (niektóre sytuacje obejmujące inne usługi, takie jak Internet Information Service, mogą wymagać wyższego poziomu uprawnień).  
  
 Gdy program Visual Studio jest uruchomiony, Menedżer debugowania procesów (PDM) śledzi procesy debugowania na komputerze lokalnym. Zdalnie, program o nazwie msvsmon.exe jest uruchamiany przez dewelopera w celu obsługi zdalnego debugowania i udostępnienia PDM. (Należy pamiętać, że msvsmon.exe nie jest usługą i należy ją uruchomić ręcznie, aby włączyć debugowanie zdalne na tym komputerze). Gdy program Visual Studio (lub msvsmon.exe) nie jest uruchomiony, żadne procesy nie są śledzone na potrzeby debugowania.  
  
 Oznacza to, że programista może debugować programy, które uruchomiły bez specjalnych uprawnień. Deweloper może nawet debugować procesy uruchomione przez kogoś innego, jeśli inna osoba jest członkiem tej samej grupy zabezpieczeń. Aby włączyć debugowanie zdalne, należy jedynie skopiować niezbędne pliki na maszynę zdalną i rozpocząć msvsmon.exe (zobacz [Konfigurowanie narzędzi zdalnych na urządzeniu,](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) Aby uzyskać więcej informacji).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)   
 [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md)   
 [Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
