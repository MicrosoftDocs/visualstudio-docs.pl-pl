---
title: Kwestie bezpieczeństwa | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713052"
---
# <a name="security-issues"></a>Problemy z zabezpieczeniami
Aby debugować program przy użyciu programu Visual Studio, tylko uprawnienia potrzebne są te same te same, które deweloper wymaga do uruchomienia programu. Obejmuje to zdalne debugowanie w większości sytuacji. Niektóre sytuacje związane z innymi usługami, takimi jak internetowa usługa informacyjna, mogą wymagać wyższego poziomu uprawnień.

 Gdy program Visual Studio jest uruchomiony, menedżer debugowania procesów (PDM) śledzi procesy debugowania na komputerze lokalnym. Zdalnie program o nazwie *msvsmon.exe* jest uruchamiany przez dewelopera do obsługi zdalnego debugowania i udostępniania pdm. *(msvsmon.exe* nie jest usługą i należy uruchomić ręcznie, aby włączyć zdalne debugowanie na tym komputerze.) Gdy program Visual Studio (lub *msvsmon.exe)* nie jest uruchomiony, żadne procesy nie są śledzone do debugowania.

 Deweloper może debugować programy, które rozpoczęły bez specjalnych uprawnień. Deweloper może nawet debugować procesy uruchamiane przez inną osobę, jeśli ta inna osoba jest członkiem tej samej grupy zabezpieczeń. Aby włączyć zdalne debugowanie, konieczne jest tylko skopiowanie wymaganych plików na komputer zdalny i uruchomienie *pliku msvsmon.exe.* Aby uzyskać więcej informacji, zobacz [Zdalne debugowanie](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Zobacz też
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
- [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md)
- [Debugowanie zdalne](../../debugger/remote-debugging.md)
