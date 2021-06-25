---
title: Debugowanie | Microsoft Docs
description: Dowiedz się, jak aparat debugowania współpracuje z interpreterem lub systemem operacyjnym w celu zapewnienia usług, takich jak kontrola wykonywania, punkty przerwania i ocena wyrażeń.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 87c4648ed37ef4fad0d79b7048593ff0c5b7d6d0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905712"
---
# <a name="debug-engine"></a>Aparat debugowania
Aparat debugowania (DE) współpracuje z interpreterem lub systemem operacyjnym w celu zapewnienia usług debugowania, takich jak kontrola wykonywania, punkty przerwania i ocena wyrażeń. De jest odpowiedzialny za monitorowanie stanu debugowany program. W tym celu de używa dowolnych metod są dostępne dla niego w obsługiwanym środowisku uruchomieniowym, czy z procesora CPU lub z interfejsów API dostarczonych przez środowisko uruchomieniowe.

 Na przykład środowisko uruchomieniowe języka wspólnego (CLR) dostarcza mechanizmy do monitorowania uruchomionego programu za pośrednictwem interfejsów ICorDebugXXX. De, który obsługuje CLR używa odpowiednich interfejsów ICorDebugXXX do śledzenia zarządzanego programu kodu, który jest debugowany. Następnie przekazuje wszelkie zmiany stanu do menedżera debugowania sesji (SDM), który przekazuje te informacje do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska IDE.

> [!NOTE]
> Aparat debugowania jest przeznaczony dla określonego środowiska uruchomieniowego, czyli systemu, w którym jest uruchamiany debugowany program. ClR to środowisko uruchomieniowe kodu zarządzanego, a środowisko uruchomieniowe Win32 jest dla natywnych aplikacji systemu Windows. Jeśli język, który utworzysz, może być używany jako cel jednego z tych dwóch środowisk uruchomieniowych, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] program dostarcza już niezbędne aparaty debugowania. Wystarczy zaimplementować ewaluator wyrażeń.

## <a name="debug-engine-operation"></a>Operacja aparatu debugowania
 Usługi monitorowania są implementowane za pośrednictwem interfejsów DE i mogą powodować przejście pakietu debugowania między różnymi trybami operacyjnymi. Aby uzyskać więcej informacji, zobacz [Tryby operacyjne](../../extensibility/debugger/operational-modes.md). Zwykle istnieje tylko jedna implementacja DE na środowisko uruchomieniowe.

> [!NOTE]
> Chociaż istnieją oddzielne implementacje DE dla języka Transact-SQL i [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] , język VBScript i [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] współużytkują jeden język DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugowanie umożliwia aparatom debugowania uruchamianie jednego z dwóch sposobów: w tym samym procesie co powłoka lub w tym samym procesie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] co debugowany program docelowy. Ta druga forma zwykle występuje, gdy debugowany proces jest w rzeczywistości skryptem uruchomionym w interpreterze. Aparat debugowania musi mieć niesłyszącą wiedzę na temat interpretera w celu monitorowania skryptu. W tym przypadku interpreter jest w rzeczywistości środowiskiem uruchomieniowym; Aparaty debugowania są dla określonych implementacji środowiska uruchomieniowego. Ponadto implementację jednego de można podzielić między granice procesu i maszyny (na przykład debugowania zdalnego).

 De uwidacznia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsy debugowania. Cała komunikacja jest za pośrednictwem com. Niezależnie od tego, czy de jest ładowany w procesie, poza procesem lub na innym komputerze, nie ma to wpływu na komunikację składników.

 De współpracuje ze składnikiem ewaluatora wyrażeń, aby umożliwić de dla tego konkretnego środowiska uruchomieniowego, aby zrozumieć składnię wyrażeń. De współpracuje również ze składnikiem obsługi symboli, aby uzyskać dostęp do symbolicznych informacji debugowania generowanych przez kompilator języka. Aby uzyskać więcej informacji, zobacz [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md) i [Dostawca symboli](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Wyrażenie](../../extensibility/debugger/expression-evaluator.md)
- [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)
