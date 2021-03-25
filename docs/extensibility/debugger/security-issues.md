---
title: Problemy z zabezpieczeniami | Microsoft Docs
description: Dowiedz się więcej o uprawnieniach wymaganych do debugowania programu za pomocą programu Visual Studio, w tym zdalne debugowanie i sytuacje, które obejmują inne usługi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1994a4a95d005edf4a71df3a1bb899522ecec137
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070430"
---
# <a name="security-issues"></a>Problemy z zabezpieczeniami
Aby debugować program przy użyciu programu Visual Studio, wymagane są te same uprawnienia, które są wymagane przez dewelopera do uruchamiania programu. Obejmuje to zdalne debugowanie w większości sytuacji. Niektóre sytuacje, w tym inne usługi, takie jak Internet Information Service, mogą wymagać wyższego poziomu uprawnień.

 Gdy program Visual Studio jest uruchomiony, Menedżer debugowania procesów (PDM) śledzi procesy debugowania na komputerze lokalnym. Zdalnie, program o nazwie *msvsmon.exe* jest uruchamiany przez dewelopera w celu obsługi zdalnego debugowania i udostępnienia PDM. (*msvsmon.exe* nie jest usługą i należy ją uruchomić ręcznie, aby włączyć debugowanie zdalne na tym komputerze). Gdy program Visual Studio (lub *msvsmon.exe*) nie jest uruchomiony, żadne procesy nie są śledzone na potrzeby debugowania.

 Deweloper może debugować programy uruchamiane bez specjalnych uprawnień. Deweloper może nawet debugować procesy uruchomione przez kogoś innego, jeśli inna osoba jest członkiem tej samej grupy zabezpieczeń. Aby włączyć debugowanie zdalne, konieczne jest tylko skopiowanie wymaganych plików na maszynę zdalną i uruchomienie *msvsmon.exe*. Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Zobacz też
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
- [Menedżer debugowania procesów](../../extensibility/debugger/process-debug-manager.md)
- [Debugowanie zdalne](../../debugger/remote-debugging.md)
