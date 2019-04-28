---
title: Problemy z zabezpieczeniami | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f68db1a4c6fb3ea2a7f9542c1a9d2d313359554
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913111"
---
# <a name="security-issues"></a>Problemy z zabezpieczeniami
Aby debugować programu przy użyciu programu Visual Studio, tylko wymagane uprawnienia są same dewelopera wymaga, aby uruchomić program. W tym zdalnego debugowania w większości sytuacji. Czasami obejmujące innych usług, takich jak Internet Information Services mogą wymagać wyższego poziomu uprawnień.

 Po uruchomieniu programu Visual Studio Menedżer debugowania procesów (menedżerów PDM) śledzi debugowanie procesów na komputerze lokalnym. Zdalnie, program o nazwie *msvsmon.exe* została uruchomiona przez dewelopera obsługę zdalnego debugowania i udostępnić menedżerów PDM. (*msvsmon.exe* nie jest usługą i musi zostać uruchomione ręcznie włączyć zdalne debugowanie na tym komputerze.) Gdy program Visual Studio (lub *msvsmon.exe*) jest nie jest uruchomiona, żadne procesy nie są śledzone dla debugowania.

 Projektant umożliwia debugowanie programów, które zostały rozpoczęte o żadne specjalne uprawnienia. Deweloper może nawet debugować procesy uruchomione przez innego użytkownika, jeśli inne osoba jest członkiem tej samej grupy zabezpieczeń. I włączyć zdalne debugowanie, konieczne jest tylko do skopiowanie wymaganych plików do maszyny zdalnej i rozpocząć *msvsmon.exe*. Aby uzyskać więcej informacji, zobacz [zdalne debugowanie](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Zobacz także
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
- [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md)
- [Debugowanie zdalne](../../debugger/remote-debugging.md)
